# Nax
## TCN | Sep 12, 2022

Upon visiting the site, we are presented with ASCII art and a list of words that look like chemical elements on a periodic table. Don't bother translating, I did it and it didn't lead to anything

`Silver - Mercury - Tantalum - Antimony - Polonium - Palladium - Mercury - Platinum - Lawrencium`

After reading a writeup, we get the number values instead and convert these charcodes to ASCII
`47 80 73 51 84 46 80 78 103`
Which prints `/PI**.**g`

This is a P*** encoded image which we need to decode

We find this by running exiftool

After decoding the value, we get to a username and the password is split by the %
Username: `n*********n`
Password: `n**************Y`

We use a metasploit exploit for RCE (not available in msf6 search, the exploit is `exploit/linux/http/n****s_**_plugins_check_plugin_*************_rce`)

We set environment variables and just run