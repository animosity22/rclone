---
title: "Mega"
description: "Rclone docs for Mega"
date: "2018-04-09"
---

<i class="fa fa-archive"></i> Mega
-----------------------------------------

Paths are specified as `remote:path`

Paths may be as deep as required, eg `remote:directory/subdirectory`.

Here is an example of how to make a remote called `remote`.  First run:

     rclone config

This will guide you through an interactive setup process:

```
No remotes found - make a new one
n) New remote
s) Set configuration password
q) Quit config
n/s/q> n
name> remote
Type of storage to configure.
Choose a number from below, or type in your own value
 1 / Alias for a existing remote
   \ "alias"
[snip]
14 / Mega
   \ "mega"
[snip]
23 / http Connection
   \ "http"
Storage> mega
User name
user> you@example.com
Password.
y) Yes type in my own password
g) Generate random password
n) No leave this optional password blank
y/g/n> y
Enter the password:
password:
Confirm the password:
password:
Remote config
--------------------
[remote]
type = mega
user = you@example.com
pass = *** ENCRYPTED ***
--------------------
y) Yes this is OK
e) Edit this remote
d) Delete this remote
y/e/d> y
```

Once configured you can then use `rclone` like this,

List directories in top level of your Mega

    rclone lsd remote:

List all the files in your Mega

    rclone ls remote:

To copy a local directory to an Mega directory called backup

    rclone copy /home/source remote:backup

### Modified time and hashes ###

Mega does not support modification times or hashes yet.

### Limitations ###

This backend uses the [go-mega go
library](https://github.com/t3rm1n4l/go-mega) which is an opensource
re-implementation of the [mega C++
SDK](https://github.com/meganz/sdk).  There doesn't appear to be any
documentation for the mega protocol beyond the C++ source code so
there are likely quite a few errors still remaining in this library.

Mega allows duplicate files which may confuse rclone.
