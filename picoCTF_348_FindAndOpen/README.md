# FindAndOpen

This CTF is available [here](https://play.picoctf.org/practice/challenge/348?category=4&page=1&solved=1).

It gives us a ZIP file that has to be unlocked using a password hidden in another _tracefile_, that is a packet capture.

I tried unzipping the archive, but it is password protected. I'll try analyzing the pcap now using wireshark.

---

There were a few base64-ish strings. As a base64 string needs to be a multiple of 3 in length, I tried appending `=`'s and prepending `a`'s to get the secret password in one of them, and extracted the flag.
