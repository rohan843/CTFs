# endianness-v2

This CTF is available [here](https://play.picoctf.org/practice/challenge/415?category=4&page=1&solved=1).

It gives us a data file of an unsure format. I'm analyzing the file now.

---

I have compared the file to various file format byte headers. Based on this, I have confirmed that the file has each _word_ reversed. I.e., I need to reverse each 4-byte groups. It should give me a JFIF file.

---

I reversed the bytes in 4-sized groups using `xxd` and `awk` to get a JFIF image, that revealed the flag.
