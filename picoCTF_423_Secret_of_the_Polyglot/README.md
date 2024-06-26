# Secret of the Polyglot

This CTF is available [here](https://play.picoctf.org/practice/challenge/423?category=4&page=1&solved=1).

It gives us a file named `flag2of2-final.pdf` along with a description that suggests we should analyse the file to determine its format.

---

On a simple `file` command usage, we see that this is a PNG file. More analysis with `exiftool` informs us that there is extra data appended to the file, which from `xxd` hex output seems to be a PDF file.

On opening the png, we see the starting portion of a flag: `picoCTF{f1u3n7_`
