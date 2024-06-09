# tunn3l v1s10n

This CTF is available [here](https://play.picoctf.org/practice/challenge/112?category=4&page=1&solved=1).

It gives us a file named `tunn3l_v1s10n`, and asks us to find the flag in it.

Using `exiftool` I have determined that this is a bitmap image (`BMP`), but on opening it a message shows up that the header size is unsupported. Possibly the header is corrupt, as the output of `exiftool` was also odd.
