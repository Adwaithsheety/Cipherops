---
cover: ../../../.gitbook/assets/Blog banner (6).png
coverY: -36
---

# 🦸 From Zero to Hero: Navigating Linux Commands Like a Pro

Here is a list of essential Linux commands for various operations:

### <mark style="color:green;">File Operations</mark>:

* `ls: Lists all files and directories in the present working directory.`
* `ls -R: Lists files in sub-directories as well.`
* `ls -a: Shows hidden files.`
* `ls -al: Lists files and directories with detailed information.`
* `cd directoryname: Changes the directory.`
* `cd ..: Moves one level up.`
* `pwd: Displays the present working directory.`
* `cat > filename: Creates a new file.`
* `cat filename: Displays the file content.`
* `cat file1 file2 > file3: Joins two files and stores the output in a new file.`
* `touch filename: Creates or modifies a file.`
* `rm filename: Deletes a file.`
* `cp source destination: Copies files from the source path to the destination path.`
* `mv source destination: Moves files from the source path to the destination path.`
* `find / -name filename: Finds a file or a directory by its name starting from root.`
* `file filename: Determines the file type.`
* `less filename: Views the file content page by page.`
* `head filename: Views the first ten lines of a file.`
* `tail filename: Views the last ten lines of a file.`
* `lsof: Shows which files are opened by which process.`
* `du -h --max-depth=1: Shows the size of each directory.`

### <mark style="color:green;">Directory Operations</mark>:

* `mkdir directoryname: Creates a new directory in the present working directory.`
* `rmdir directoryname: Deletes a directory.`
* `cp -r source destination: Copies directories recursively.`
* `mv olddir newdir: Renames directories.`
* `find / -type d -name directoryname: Finds a directory starting from root.`

### <mark style="color:green;">Process Operations</mark>:

* `ps: Displays currently active processes.`
* `top: Displays all running processes.`
* `kill pid: Kills the process with the given PID.`
* `pkill name: Kills the process with the given name.`
* `bg: Resumes suspended jobs without bringing them to the foreground.`
* `fg: Brings the most recent job to the foreground.`
* `fg n: Brings job n to the foreground.`
* `renice +n [pid]: Changes the priority of a running process.`

### <mark style="color:green;">File Permissions</mark>:

* `chmod octal filename: Change the permissions of a file.`
* `chown ownername filename: Change file owner.`
* `chgrp groupname filename: Change group owner.`

### <mark style="color:green;">Networking</mark>:

* `ping host: Ping a host and output results.`
* `whois domain: Get whois information for a domain.`
* `dig domain: Get DNS information for a domain.`
* `netstat -pnltu: Display various network related information.`
* `ifconfig: Displays IP addresses of all network interfaces.`
* `ssh user@host: Remote login into the host as a user.`
* `scp: Transfers files between hosts over SSH.`
* `wget url: Download files from the web.`
* `curl url: Sends a request to a URL and returns the response.`
* `traceroute domain: Prints the route that a packet takes to reach the domain.`
* `mtr domain: Combines the functionality of traceroute and ping.`
* `ss: Investigates sockets.`
* `nmap: Network exploration tool and security scanner.`

### <mark style="color:green;">Archives and Compression</mark>:

* `tar cf file.tar files: Create a tar archive containing files.`
* `tar xf file.tar: Extract files from a tar archive.`
* `gzip file: Compresses a file.`
* `gzip -d file.gz: Decompresses a file.`
* `zip -r file.zip files: Create a zip archive.`
* `unzip file.zip: Extract the contents of a zip file.`

### <mark style="color:green;">Text Processing</mark>:

* `grep pattern files: Search for a pattern in files.`
* `grep -r pattern dir: Search recursively for a pattern in a directory.`
* `echo 'text': Prints text.`
* `sed 's/string1/string2/g' filename: Replaces string1 with string2 in a file.`
* `diff file1 file2: Compares two files and shows the differences.`
* `wc filename: Count lines, words, and characters in a file.`
* `awk: A versatile programming language for working on files.`
* `sed -i 's/string1/string2/g' filename: Replace string1 with string2 in a file.`
* `cut -d':' -f1 /etc/passwd: Cut out the first field of each line in /etc/passwd.`

### <mark style="color:green;">Disk Usage</mark>:

* `df: Shows disk usage.`
* `du: Shows directory space usage.`
* `free: Show memory and swap usage.`
* `whereis app: Show possible locations of an app.`

### <mark style="color:green;">System Info</mark>:

* `date: Show the current date and time.`
* `cal: Show this month's calendar.`
* `uptime: Show current uptime.`
* `w: Display who is online.`
* `whoami: Who you are logged in as.`
* `uname -a: Show kernel information.`
* `df -h: Disk usage in a human-readable format.`
* `du -sh: Disk usage of the current directory in a human-readable format.`
* `free -m: Show free and used memory in MB.`

### <mark style="color:green;">Package Installations</mark>:

* sudo `apt-get update: Updates package lists for upgrades.`
* `sudo apt-get upgrade: Upgrades all upgradable packages.`
* `sudo apt-get install pkgname: Install a package.`
* `sudo apt-get remove pkgname: Removes a package`.

### <mark style="color:green;">Others (mostly used in scripts)</mark>:

* `command1 ; command2: Run command1 and then command2.`
* `command1 && command2: Run command2 if command1 is successful.`
* `command1 || command2: Run command2 if command1 is not successful.`
* `command &: Run command in the background.`

### <mark style="color:green;">Version Control (Git commands)</mark>:

* `git init: Initialize a local Git repository.`
* `git clone url: Create a local copy of a remote repository.`
* `git add filename: Add a file to the staging area.`
* `git commit -m "Commit message": Commit changes with a message.`
* `git status: Check the status of the working directory.`
* `git pull: Pull latest changes from the remote repository.`
* `git push: Push changes to the remote repository.`
* `git branch: List all local branches.`
* `git branch branchname: Create a new branch.`
* `git checkout branchname: Switch to a branch.`
* `git merge branchname: Merge a branch into the active branch.`
* `git stash: Stash changes in a dirty working directory.`
* `git stash apply: Apply changes from a stash.`
* `git log: View commit history.`
* `git reset: Reset your HEAD pointer to a previous commit.`
* `git rm filename: Remove a file from version control.`
* `git rebase: Reapply commits on top of another base tip.`
* `git revert: Create a new commit that undoes all the changes made in a particular commit.`
* `git cherry-pick commitID: Apply the changes introduced by some existing commits.`

### <mark style="color:green;">Environment Variables</mark>:

* `env: Display all environment variables.`
* `` `echo $V ``

<mark style="color:green;">ARIABLE\`: Display the value of an environment variable</mark>.

* `export VARIABLE=value: Set the value of an environment variable.`
* `alias new_command='old_command options': Create a new command that executes the old command with the specified options.`
* `echo $PATH: Print the PATH environment variable.`
* `export PATH=$PATH:/new/path: Add /new/path to the PATH.`

### <mark style="color:green;">Job Scheduling (Cron Jobs)</mark>:

* `crontab -l: List all your cron jobs.`
* `crontab -e: Edit your cron jobs.`
* `crontab -r: Remove all your cron jobs.`
* `crontab -v: Display the last time you edited your cron jobs.`
* `crontab file: Install a cron job from a file.`
* `@reboot command: Schedule a job to run at startup.`

### <mark style="color:green;">Package Installations (using pip, a Python package installer)</mark>:

* `pip install packagename: Install a Python package.`
* `pip uninstall packagename: Uninstall a Python package.`
* `pip freeze > requirements.txt: Freeze the installed packages into a requirements file.`
* `pip install -r requirements.txt: Install packages from a requirements file.`

### <mark style="color:green;">Shell Scripting</mark>:

* `#!/bin/bash: Shebang line to specify the script interpreter.`
* `$0, $1, ..., $9, ${10}, ${11}: Script arguments.`
* `if [condition]; then ... fi: if statement in Bash scripts.`
* `for i in {1..10}; do ... done: for loop in Bash scripts.`
* `while [condition]; do ... done: while loop in Bash scripts.`
* `function name() {...}: Define a function.`

### <mark style="color:green;">System Monitoring and Performance</mark>:

* `iostat: Reports CPU statistics and input/output statistics for devices, partitions, and network filesystems.`
* `vmstat: Reports information about processes, memory, paging, block IO, traps, disks, and CPU activity.`
* `htop: An interactive process viewer for Unix systems.`

### <mark style="color:green;">Search and Find</mark>:

* `locate filename: Find a file by its name.`
* `whereis programname: Locate the binary, source, and manual page files for a command.`
* `which commandname: Shows the full path of shell commands.`

### <mark style="color:green;">Compression / Archives</mark>:

* `tar -cvf archive.tar dirname/: Create a tar archive.`
* `tar -xvf archive.tar: Extract a tar archive.`
* `tar -jcvf archive.tar.bz2 dirname/: Create a compressed bz2 archive.`
* `tar -jxvf archive.tar.bz2: Extract a bz2 archive.`

### <mark style="color:green;">Disk Usage</mark>:

* `dd if=/dev/zero of=/tmp/output.img bs=8k count=256k: Create a file of a certain size for testing disk speed.`
* `hdparm -Tt /dev/sda: Measure the read speed of your hard drive.`

### <mark style="color:green;">Others</mark>:

* `yes > /dev/null &: Use this command to push a system to its limit.`
* `:(){ :|:& };::: A fork bomb – handle with care. Do not run this command on a production system.`

{% embed url="https://www.commandlinefu.com/commands/browse" %}

Remember, you can always use the `man` command (e.g., `man ls`) to get more information about each command.
