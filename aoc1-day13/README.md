# AoC 1 Day 13 -- Accumulate
## TCN | Sep 5 2022

We run an [Nmap scan](./nmap.log) and [Gobuster scan](./gobuster.log)
The ports 80 (web server) and 3389 (RDP) come out
This is seemingly also a Windows box

Answer 1

Gobuster scan at [gobuster.log](./gobuster.log)

---

We find that this is a WordPress site and a username: `w__e`.
In a post about Ready Player One, he mentions that he misspells his character's avatar. This appears to be `p______l`.
He also writes this in a comment, so you don't have to google it.
We can log into WordPress but that doesn't have anything
However, if we login to the machine via RDP on port 3389 (found earlier) using the same credentials, we get access to the Windows .

---

Answer 2

We get user.txt on the desktop which has the flag:
`THM{HA____________E}`

---

Answer 3

After reading a writeup, I found out that you can get an admin shell by running the file `hhupd.exe` on desktop as administrator. This prompts a password prompt.
Click `Show more details` and then click `Show more information about the publisher's certificate`. Click the link `VeriSign Commercial Software Publishers CA`. Click `No` to close the prompt and you will see that Internet Explorer has opened.
Click the `cog icon > File > Save as` to get a save as box. Open cmd.exe and get an admin shell
Get the contents of C:\Users\Administrator\Desktop\root.txt using `more`. This gives the flag:
`THM{C________________________N}`
