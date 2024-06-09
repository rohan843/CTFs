# tunn3l v1s10n

This CTF is available [here](https://play.picoctf.org/practice/challenge/112?category=4&page=1&solved=1).

It gives us a file named `tunn3l_v1s10n`, and asks us to find the flag in it.

Using `exiftool` I have determined that this is a bitmap image (`BMP`), but on opening it a message shows up that the header size is unsupported. Possibly the header is corrupt, as the output of `exiftool` was also odd.

I will lookup the header format of a `BMP` file.

---

Ok, I followed the format given [here](http://www.ece.ualberta.ca/~elliott/ee552/studentAppNotes/2003_w/misc/bmp_file_format/bmp_file_format.htm) and corrected the size of `InfoHeader` to 40 (its equivalent in hex).

This allowed the image to be opened in viewer, but the only text in the image was `notaflag{sorry}` 😑.

---

I ran `zsteg` on the bitmap image. It said that there was extra data after the image end. I have extracted that data using `dd` but still have no idea what this data is. Right now, it just seems to be random bytes that break `zsh` display when output using `cat`.

---

Finally, I had to refer to a [writeup](https://ctftime.org/writeup/28157) but it turns out that the image height was also wrong in the binary. Increasing it displayed the flag.
