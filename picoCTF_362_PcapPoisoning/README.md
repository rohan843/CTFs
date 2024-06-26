# PcapPoisoning

This CTF can be found [here](https://play.picoctf.org/practice/challenge/362?category=4&page=1&solved=1).

It gives us a packet capture that I have opened in wireshark.

---

One of the initial packets is a malformed DNS packet, whose text says `flagisclose`.

---

It seemed like a port scan at first. The TCP packets went 