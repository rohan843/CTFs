# scrambled-bytes

This CTF is available [here](https://play.picoctf.org/practice/challenge/206?category=4&page=1&solved=1).

It gives us a python script that was used to transmit a flag, and a packet capture of the duration, and asks us to find the flag.

---

On analysing the python script, we see that the flag was in a file, that was sent using UDP to a specific port and ip address. However, before sending the file, its bits were randomly shuffled and XOR'ed with random bytes. This is a problem.