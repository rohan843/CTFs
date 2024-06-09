# tunn3l v1s10n

This CTF is available [here](https://play.picoctf.org/practice/challenge/112?category=4&page=1&solved=1).

It gives us a file named `tunn3l_v1s10n`, and asks us to find the flag in it.

Using `exiftool` I have determined that this is a bitmap image (`BMP`), but on opening it a message shows up that the header size is unsupported. Possibly the header is corrupt, as the output of `exiftool` was also odd.

I will lookup the header format of a `BMP` file.

---

Ok, I followed the format given [here](http://www.ece.ualberta.ca/~elliott/ee552/studentAppNotes/2003_w/misc/bmp_file_format/bmp_file_format.htm) and corrected the size of `InfoHeader` to 40 (its equivalent in hex).

This allowed the image to be opened in viewer, but the only text in the image was `notaflag{sorry}` 😑.
