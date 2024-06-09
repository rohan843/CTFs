# CTF Strategies

Here, various strategies that can be followed in CTFs are provided. Each heading and sub-text provides a situation where we might be (such as having an ASCII encoded text file) and then some things that can be done at that point.

The headings will be alphabetical.

## Contents

- [CTF Strategies](#ctf-strategies)
  - [Contents](#contents)
  - [Directories](#directories)
  - [Exotic Files](#exotic-files)
  - [Image Files (BMP, PNG, JPG, ...)](#image-files-bmp-png-jpg-)
  - [Random Looking File/Binary Data](#random-looking-filebinary-data)
  - [Text Data - ASCII](#text-data---ascii)

## Directories

Directory contents can be browsed using the usual `cd` and `ls -a`. For viewing all files at once, use `ls -R`, and for viewing files in a fuzzy string matching mode, use the tool [`fzf`](https://github.com/junegunn/fzf).

Lookout for suspicious names like:

1. `hidden`
2. `flag`

And also for actionable files:

1. text files (`.txt`)
2. `.png|jpg|bmp`
3. `.bin` or other binaries
4. ELF files
5. Code files

## Exotic Files

There might be unconventional files provided at times, such as powerpoint files (`.ppt`). These are usually ZIP archives and can be unzipped to reveal usual files and data.

For an exact reference, google the file extension to learn more about the file format.

## Image Files (BMP, PNG, JPG, ...)

Image files almost always require some sort of steganalysis. When such files are received, use `exiftool` to get information about them. Often, PNGs will have extra data appended after the `IEND` chunk (after image end).

A tool that can be used for steganalysis is `zsteg`. Use the command `zsteg -a <file-name>` to get every possible extraction applied to the file. Moreover, `zsteg` will also report the byte offset in a PNG should extra data be appended which then can be extracted using `dd`.

Also, `steghide` and `stegseek` may be used, esp. in case some passphrase is available or if `zsteg` fails. Try `stegseek --seed <file-name>` to check if any one of $2^{32}$ possible seeds were used. This can help to determine if `steghide` was used to hide data.

An important note in bitmap (BMP) files is that they may have mangled header information, such as incorrect height or width. Use `hexedit` to increase the heights and widths just to check if any parts of the image were hidden from view. An online reference for the BMP format can be useful for this: [https://en.wikipedia.org/wiki/BMP_file_format#Bitmap_file_header](https://en.wikipedia.org/wiki/BMP_file_format#Bitmap_file_header).

## Random Looking File/Binary Data

Sometimes weird files may be extracted/received that have no extension or magic bytes in the header. These might be ZIP archives. Try to unzip them.

Binary files can be viewed using `xxd`. Try `xxd -g 1 <file-name> | less` or `xxd -R always -g 1 <file-name> | less -R` if the terminal supports 8-bit color display to view them.

## Text Data - ASCII

If we have ascii text data, it might be [caesar ciphered](https://cryptii.com/pipes/caesar-cipher) or [base64 encoded](https://www.base64decode.org/). A give away of base64 is `=` signs at the end.
