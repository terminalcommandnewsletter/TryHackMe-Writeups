# Vulnversity Writeup
## TCN | Aug 31, 2022

### Task 2
We run nmap with -p- to scan all ports, however all ports are within port 5000

Running ```nmap -A -oG nmap.log -p-5000 [IP]``` (for greppable output to nmap.log with Nmap Scripting Engine running scripts against ports) returns the contents in [nmap.log](./nmap.log)

From scan results we can see that *6* ports are open, *3._.__* version of Squid Proxy is running, the web server is running on port *3___* and the most likely OS is *Ubuntu*.

For other general questions, the answers are below:
nmap will scan *400* ports if -p-400 was used.
Using -n, *DNS* will not resolve.

---

### Task 3
We run gobuster. I'll be using the directory-list-2.3-medium.txt wordlist
From the scans, */internal* contains an upload page so we don't need to continue scanning

Read the log at [gobuster.log](./gobuster.log)

---

### Task 4
Trying to upload php-reverse-shell.php (from PentestMonkey) doesn't work because .php is not allowed.
Here we need to use BurpSuite to bruteforce extensions for a reverse shell.
We find out that *phtml* is allowed. So what we need to do is to upload the reverse shell with a .phtml extension.
After uploading the reverse shell and visiting [IP]/internal/uploads/[NAME OF SHELL FILE] and running a netcat listener with ```sudo nc -lvnp [PORT IN REVERSE SHELL]``` we get a shell back.

To find the name of the user running the server, we cat /etc/passwd and find any unusual users.
The user running this server is *bill*.

Going into his home directory, we can read the flag.

## Flag: 8xx7xxxxbexxxxxxxx63xxx0xxxxxxxb

---

### Task 5
We look for unusual SUID binaries with ```find / -perm -u=s 2>/dev/null```.
We find */bin/systemctl*.
We look up systemctl on GTFOBins
After customising the SUID code to run ```cat /root/root.txt``` instead of ```id```.
We get the flag.

## Flag: a58xxxxxxxxxx27xxxxx3xxxxxxxxxx5

# END OF ROOM
