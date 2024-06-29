# File types

This CTF is available [here](https://play.picoctf.org/practice/challenge/268?category=4&page=1&solved=1).

It gives us a file with the extension of `pdf`, but it actually is a shell script. I ran it, and it produced file called `flag`, but the contents were not ascii. I'll go through the code next.

---

It seems that the contents of the shell script are coded to output a file. This file contains the flag information, but is a `current ar archive`. I'll try extracting the contents by looking for a suitable command.
