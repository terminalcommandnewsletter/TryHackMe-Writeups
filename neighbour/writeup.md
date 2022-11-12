# Neighbour | TryHackMe
## TCN | Nov 12, 2022
---

## Visiting the site
When we visit the site, we are greeted with this login page:
![Login page that says "Don't have an account? Use the guest account (Ctrl+U) with an arrow (inserted by the author) with text "<-- View page source"](./writeup/login_page.png)

From this login page, we can tell that guest credentials will be in the source code of the page (since Ctrl+U is the keyboard shortcut to open page source)

Upon opening the source code, we find this HTML comment on line 34:
![Source code blurred to emphasize HTML comment on line 34 `<!-- use guest:guest credentials until registration is fixed. "admin" user account is off limits!!!!! !-->`](./writeup/source_code.png)

---
## Signing in
Okay, so the user `"admin"` is off limits and we have the credentials for the `"guest"` user account `(guest:guest)`.

After logging in with those credentials, we see the page as below
![A browser screenshot with the URL "http://MACHINE_IP/profile.php?user=guest". This is connected using a line (inserted by author) to the word "guest" in text "Hi guest. Welcome to our site. Try not to peep your neighbor's profile". Below this text, there is a button "Sign out of your account"](./writeup/profile.png)
We see the text `"Hi *guest*. Welcome to our site. Try not to peep your neighbor's profile"`. But let us have a look at the URL. `"http://MACHINE_IP/profile.php?user=guest"`

---
## Exploiting the vulnerability
There is a parameter `"user"` with the value `"guest"`. Perhaps this username is being inserted into the page text. Furthermore, will this parameter lead to insecure authentication and show something sensitive only accessible to certain accounts, e.g. admins? Well.. the answer is **YES**!

If we change this value from `"guest"` to `"admin"` (a username we found in the source code), we get access to the admin account and see the flag.

![The same page as earlier except the text says "Hi, **admin**. Welcome to your site. The flag is" followed by a flag blurred by the author](./writeup/admin_flag.png)

---
## Room Complete!

That ends the room.

[My Twitter @macnlinux_blog](http://twitter.com/macnlinux_blog)

[My Website](http://tercmd.com)

[My Newsletter](http://newsletter.tercmd.com)