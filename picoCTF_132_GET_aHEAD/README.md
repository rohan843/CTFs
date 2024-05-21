# GET aHEAD

This CTF is available [here](https://play.picoctf.org/practice/challenge/132?page=1&solved=1).

It gives us a link: `http://mercury.picoctf.net:15931/` and asks us to find the flag on this server.

---

I have `curl`ed the HTML response from the server into a file `red.html`. On Firefox, it simply displays a webpage with a red background (hence the name of the file) with 2 buttons that change the color of the page to blue or to red.
