# advanced-potion-making

This CTF can be found [here](https://play.picoctf.org/practice/challenge/205?category=4&page=1&solved=1).

It gives us some file that has been "corrupted". By looking at the file in text mode and in binary mode, because of the presence of `IEND` at the end and `.PB....` at the beginning, its a good chance its a corrupted PNG file. I'll try correcting it now.

---

I've restored the header and am now working on chunks.

---

I have restored the `IHDR` length value to 13 (`00 00 00 0a` in hex) and opened the image. It's just a red rectangle, with no data.

It's possible there is some incorrect height/width written here, and that this is not the complete image.

---

I tried but the CRC didn't check out. I think this is a whole image, but with steganography. I used `zsteg -a`, but no info was revealed.

---

I had to see a solution for further hints, so I saw [this](https://medium.com/@matus.vaclav1/picoctf-advanced-potion-making-eff6b4ebbdcf) article. The last step was viewing the image in black and white, that displayed the flag.
