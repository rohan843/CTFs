# Wireshark twoo twooo two twoo...

This CTF is available [here](https://play.picoctf.org/practice/challenge/110?category=4&page=1&solved=1).

It gives us a packet capture with 4831 packets. I have opened it is wireshark.

---

I exported all objects detected in the capture, which were around 5480 in number. There were a number of files called `flag(<something>)`. The flag in these seem encrypted.

---

I've seen a [solution](https://www.youtube.com/watch?v=I_zb9ybAjvg) now. The hint was in the phrase `red herring`, that is used to refer to intentionally placed clues to misguide someone.

There were multiple DNS requests to subdomains of a `redshrimpandherring.com`, combining which gave us a base 64 encoded flag.