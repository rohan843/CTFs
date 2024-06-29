# File types

This CTF is available [here](https://play.picoctf.org/practice/challenge/268?category=4&page=1&solved=1).

It gives us a file with the extension of `pdf`, but it actually is a shell script. I ran it, and it produced file called `flag`, but the contents were not ascii. I'll go through the code next.

---

It seems that the contents of the shell script are coded to output a file. This file contains the flag information, but is a `current ar archive`. I'll try extracting the contents by looking for a suitable command.

---

I have extracted the contents of the `ar` directory, only to get a `cpio` archive. I'll see how to extract it next.

---

I have extracted it using the `cpio` command, to get a `bzip2` compressed data. I'll decompress it next.

---

After decompression, I got a `gzip` data, but on decompressing it, I get an error that there's an unknown suffix. It's possible that the file is corrupted. I'll try some methods to correct that.

---

The issue was in the extension. I renamed the file to have an extension of `.gz` and it extracted a file that came out to be `lzip` compressed data. I decompressed it to get `LZ4` data. Which decompressed to `LZMA` compressed data. This lead to `lzop`