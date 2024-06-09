# Matryoshka Doll

This ctf is available [here](https://play.picoctf.org/practice/challenge/129?category=4&page=1&solved=1).

It gives us a `dolls.jpg` image file. Judging by the description of matryoshka dolls and the image, I think there might be a steganography situation here.

---

I have used `exiftool` to determine the metadata of the file. Firstly, this is NOT a jpeg image but a `png` image. Second, there is trailing data after the `IEND` chunk, so definitely a steganalysis is needed.

---

I ran `zsteg -a` on the file, and it reported that the extra data at the end is a ZIP archive. I'll try extracting and un-zipping it.

---

I have extracted the appended data using `dd` and have unzipped it to get another `png` image. This image, too is an image of a doll, only smaller than the previous one. There is more trailing data. I will repeat the process I just did.

---

Another image of a doll, smaller than the first 2.

---

And, another doll image. This time, the doll size is the same, but the image itself has become low res.
