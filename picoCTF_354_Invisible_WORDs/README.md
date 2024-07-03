# Invisible WORDs

This CTF is available [here](https://play.picoctf.org/practice/challenge/354?category=4&page=1&solved=1).

It gives us a bitmap image and suggests solving the steganography. I'll apply the usual `zsteg` and `stegsolve` tactics.

---

None of the previous tactics worked, so I refered [this](https://medium.com/@niceselol/picoctf-invisible-words-2053f72cf8b6) write-up. It turns out that the file contained hidden a ZIP file, that when unzipped had a novel, that had the flag.
