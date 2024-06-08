# Trivial Falg Transfer Protocol

This is the last CTF in the picoCTF Forensics playlist, available [here](https://play.picoctf.org/playlists/16?m=130). It gives us a packet capture file called `tftp.pcapng`. I am opening this file via wireshark.

---

On a first glance, this capture contains information of 152413 packets. Almost all of these packets are of a protocol called **TFTP** (trivial file transfer protocol). I've not used this before, so I'll look up its format.

Other than TFTP, there are a few ARP and SSDP packets, small in number (tot. 18) to be manually checked.
