---
description: >-
  This installation process ensures that you have the Axiom project set up, the
  necessary dependencies installed, and Axiom-Scan integrated into your system.
---

# 🪓 Axion-Scan

Step 1: Clone the Axiom Repository

```shell
git clone https://github.com/pry0cc/axiom.git
```

Step 2: Install Dependencies

```shell
cd axiom
./install.sh
```

Step 3: Configure Axiom

```shell
./axiom-config
```

Step 4: Select Fleet Instances

```shell
./axiom-fleet select
```

Step 5: Verify Fleet Selection

```shell
./axiom-fleet list
```

Step 6: Install Axiom-Scan

```shell
./axiom-modules/install-scan.sh
```

Step 7: Verify Axiom-Scan Installation

```shell
axiom-scan --help
```

Please note that these code snippets assume a Linux-based operating system. Adjustments may be needed for different platforms. For more detailed instructions and advanced configuration options,

```shell
                                              _
  ____ __  __(_)___  ____ ___        ______________ _____
 / __ `/ |/_/ / __ \/ __ `__ \______/ ___/ ___/ __ `/ __ \
/ /_/ />  </ / /_/ / / / / / /_____(__  ) /__/ /_/ / / / /
\__,_/_/|_/_/\____/_/ /_/ /_/     /____/\___/\__,_/_/ /_/

                                    @pry0cc
                                 & @0xtavian

axiom-scan provides easy distribution of arbitrary binaries and scripts.
axiom-scan splits user-provided input files (target lists), wordlists, and configuration files and uploads them to a unique scan working directory on the remote instance.
axiom-scan combines user-provided command-line arguments with commands in the module and executes the final command on the remote instance.
axiom-scan downloads and merges scan output in a variety of different formats, specified by the extension in the module (dir, txt, csv, xml).
individual scanning operations are executed from a detached tmux session (\$module+\$timestamp) inside a unique scan working directory (/home/op/scan/\$module+\$timestamp) on the remote instances.

Usage:
   axiom-scan inputfile.txt -m ffuf -w /home/op/wordlist-on-remote-instance
   axiom-scan inputfile.txt -m ffuf -wL /home/localuser/local-wordlist-to-upload
   axiom-scan inputfile.txt -m ffuf -wD /home/localuser/local-wordlist-to-split-and-upload
   axiom-scan inputfile.txt -m nuclei -w /home/op/nuclei-templates -o outputfile.txt
   axiom-scan inputfile.txt -m nuclei --nuclei-templates /home/localuser/local-custom-nuclei-template-folder/ -anew outputfile.txt
   axiom-scan inputfile.txt -m gowitness --spinup 10 -oD gowitness-screenshots
   axiom-scan inputfile.txt -m nmapx -p- -sV -T4 -v --open -oA nampx-scan

Flags:
INPUT:
   string[]              required positional first argument must always be an input file, this can be a list of URLs, IPs, hostnames, etc
   --dont-split          do not split input file, upload entire input file to every instance (default is to split the input file)
   --dont-shuffle        do not randomize input file before uploading (default is to randomize)
MODULE:
   -m string[]           the axiom-scan module to use with the scan
   --list                print all available modules
WORDLIST:
   -w string[]                           replace _wordlist_ in module with user-provided wordlist (must be a path to a remote wordlist)
   -wL string[]                          replace _wordlist_ in module with user-provided local wordlist ( must be a path to a local wordlist)
   -wD,--distribute-wordlist string[]    replace _wordlist_ in module with user-provided local wordlist to split and upload (default does not split the wordlist)
   --nuclei-templates string[]           replace _wordlist_ in module with user-provided local folder
CONFIGURATIONS:
   --config string[]           replace _config_ in module with user-provided configuration file (must be a configuration file on the remote instances)
   --local-config string[]     replace _config_ in module with user-provided local configuration file to upload ( must be a local configuration file)
OPTIMIZATIONS:
   --skip-preflight            do not automatically remove instances that can't be reached (default removes instances from the queue that can't be reached)
   --preflight-timeout int[]   specifies the timeout (in seconds) used when connecting to the SSH server, instead of using the default 10 seconds
   --max-runtime DURATION[]    kill scan if still running after DURATION. DURATION is a floating-point number with an optional suffix: 's' for seconds (the default), 'm' for minutes, 'h' for hours, or 'd' for days.
   --disable-oneshot           by default, if a module contains the string _target_, it is executed as a one-shot module. Use this flag to force disable
OUTPUT:
   -o string[]          output as default (the first ext mentioned in the module)
   -oD/-oA string[]     output as a directory (must also be supplied in the module using "ext":"dir" or "ext":"")
   -oX string[]         output as XML/HTML (supported for nmap and masscan)(must also be supplied in the module using "ext":"xml")
   -oG string[]         output as greppable, merge and sort unique (must also be supplied in the module using "ext":"oG")
   -csv string []       output as csv, extract csv header, merge and sort unique (must also be supplied in the module using "ext":"csv")
   -anew string[]       pipe the output to anew before creating the final output file
   --quiet              do not display findings to the terminal
   --rm-logs            delete remote and local logs after the scan completes

FLEET

:
   --fleet string[]            supply fleet prefix to use (default uses instances in $HOME/.axiom/selected.conf)
   --spinup int[]              number of instances to spin up prior to scanning (default uses instances in $HOME/.axiom/selected.conf)
   --rm-when-done              delete the selected instances after the scan completes
   --shutdown-when-done        shutdown the selected instance after the scan completes
   -F string[]                 path to a custom SSH config file (default is located at $HOME/.axiom/.sshconfig)
   --cache                     do not regenerate SSH config prior to scan, instead use cached config (located at $HOME/.axiom/.sshconfig)

DEBUG:
   --debug              run with set -xv, warning: very verbose

EXTRA ARGS:
   string[]             supply additional arguments to be passed to the module
```

The usage section demonstrates various ways to use the `axiom-scan` command with different modules and options.

Here are a few examples of how to use `axiom-scan`:

```shell
axiom-scan roots.txt -m subfinder -o subs.txt --threads 3
axiom-scan subs.txt -m dnsx -resp -o dns.txt

cat dns.txt | awk '{ print $2 }' | anew ips.txt

cat ips.txt | cf-check > ips.txt

axiom-scan ips.txt -m masscan -oX masscan.xml -rate=100000
axiom-scan ips.txt -m nmap -oG nmap.txt -T4 -p- -sV
axiom-scan ips.txt -m nmap -oX nmap.xml -T4 -p- -sV

ports.py nmap.xml | anew hosts.txt

axiom-scan hosts.txt -m httpx -o http.txt

axiom-scan http.txt -m gowitness -o screenshots
axiom-scan http.txt -m ffuf -o content.csv --threads 2
```

{% code fullWidth="false" %}
```
broad explanation of the above code snippets
```
{% endcode %}

```markdown
Here's a broad explanation of the above code snippets!

1. `axiom-scan roots.txt -m subfinder -o subs.txt --threads 3`
   - This command uses Axiom-Scan to perform a distributed subdomain enumeration using the Subfinder module.
   - It takes the input file `roots.txt`, which contains a list of root domains to scan.
   - The `-o subs.txt` flag specifies the output file where the subdomains will be saved.
   - The `--threads 3` flag indicates that the scan should be performed using three parallel threads.

2. `axiom-scan subs.txt -m dnsx -resp -o dns.txt`
   - This command uses Axiom-Scan to perform a distributed DNS resolution using the DNSx module.
   - It takes the input file `subs.txt`, which contains a list of subdomains obtained from the previous scan.
   - The `-o dns.txt` flag specifies the output file where the DNS resolution results will be saved.
   - The `-resp` flag indicates that the command should include DNS response data in the output.

3. `cat dns.txt | awk '{ print $2 }' | anew ips.txt`
   - This command uses `cat` to read the contents of the `dns.txt` file.
   - It pipes the output to `awk` to extract the second column (IP addresses) from each line.
   - The resulting IP addresses are then piped to `anew` and saved in the `ips.txt` file.

4. `cat ips.txt | cf-check > ips.txt`
   - This command uses `cat` to read the contents of the `ips.txt` file.
   - It pipes the output to `cf-check` to perform Cloudflare bypass checks on the IP addresses.
   - The output, which includes the Cloudflare status of each IP, is then redirected and saved back to the `ips.txt` file.

5. `axiom-scan ips.txt -m masscan -oX masscan.xml -rate=100000`
   - This command uses Axiom-Scan to perform a distributed port scanning using the Masscan module.
   - It takes the input file `ips.txt`, which contains a list of IP addresses to scan.
   - The `-oX masscan.xml` flag specifies the output file where the scan results will be saved in XML format.
   - The `-rate=100000` flag sets the scanning rate to 100,000 packets per second.

6. `axiom-scan ips.txt -m nmap -oG nmap.txt -T4 -p- -sV`
   - This command uses Axiom-Scan to perform a distributed port scanning using the Nmap module.
   - It takes the input file `ips.txt`, which contains a list of IP addresses to scan.
   - The `-oG nmap.txt` flag specifies the output file where the scan results will be saved in Nmap's grepable format.
   - The `-T4` flag sets the scan timing template to aggressive.
   - The `-p-` flag scans all ports.
   - The `-sV` flag enables service version detection.

7. `axiom-scan ips.txt -m nmap -oX nmap.xml -T4 -p- -sV`
   - This command is similar to the previous one but saves the scan results in XML format using the `-oX` flag.

8. `ports.py nmap.xml | anew hosts.txt`
   - This command uses a custom script called `ports.py` to extract hostnames from the Nmap scan results stored in `nmap.xml`.
   - The script is piped to `anew` to filter out duplicate hostnames.
   - The filtered hostnames are saved in the `hosts.txt` file.

9. `axiom-scan hosts.txt -m httpx -o http.txt`
   - This command uses Axiom-Scan to perform a distributed HTTP probing using the HTTPx module.
   - It takes the input file `hosts.txt`, which contains a list of hostnames obtained from the previous step.
   - The `-o http.txt` flag specifies the output file where the HTTP probing results will be saved.

10. `axiom-scan http.txt -m gowitness -o screenshots`
    - This command uses Axiom-Scan to perform distributed website screenshot capture using the Gowitness module.
    - It takes the input file `http.txt`, which contains a list of HTTP URLs obtained from the previous step.
    - The `-o screenshots` flag specifies the output directory where the captured website screenshots will be saved.

11. `axiom-scan http.txt -m ffuf -o content.csv --threads 2`
    - This command uses Axiom-Scan to perform a distributed web content discovery using the FFuF module.
    - It takes the input file `http.txt`, which contains a list of HTTP URLs obtained from the previous step.

```

These examples demonstrate different scanning operations using `axiom-scan` with various modules such as `subfinder`, `dnsx`, `masscan`, `nmap`, `httpx`, `gowitness`, and `ffuf`.

Additionally, there are options to control the input, module, wordlist, configurations, optimizations, output, fleet management, and debugging.

Remember to adjust the input files, module names, and other options according to your specific use case.

Feel free to explore the different flags and experiment with the provided examples to perform distributed scanning with Axiom-Scan.

If you have any further questions or need more assistance, feel free to ask!&#x20;
