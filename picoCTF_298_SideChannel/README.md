# SideChannel

Ths CTF is available [here](https://play.picoctf.org/practice/challenge/298?category=4&page=1&solved=1).

It gives us an ELF file and asks us to figure out some pin. Once we get the pin, we are to submit it to a port via `nc` to get the flag.

---

I have gone through the file. It doesn't have a symbol table, and the reassembled code is not easy to understand. I have seen hint 1, and based on its suggestion, I now am reading about timing based side channel attacks.

---

I used a timing side channel attack to time the various pinss I entered to get the correct pin. The code provided access. I'll send this pin to the port to get the flag.
