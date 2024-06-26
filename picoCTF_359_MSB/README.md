# MSB

This challenge is available [here](https://play.picoctf.org/practice/challenge/359?category=4&page=1&solved=1).

It gives us a PNG file, with a suspected steganography.

---

I ran `zsteg` but didn't get anything. There does seem some data hidden in the image though, as it looks corrupted. I'll try editing this pic somehow.

---

Editing doesn't seem to work. I'll think of something else.

---

I saw the tool `stegsolve` used in a writeup, and used it to view the image in various planes. I then used its extract data from bit position feature to extract part of a book! Text search showed where the flag was hidden.
