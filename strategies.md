# CTF Strategies

Here, various strategies that can be followed in CTFs are provided. Each heading and sub-text provides a situation where we might be (such as having an ASCII encoded text file) and then some things that can be done at that point.

The headings will be alphabetical.

## Contents

- [CTF Strategies](#ctf-strategies)
  - [Contents](#contents)
  - [Directories](#directories)
  - [Disk Images](#disk-images)
  - [Exotic Files](#exotic-files)
  - [Image Files (BMP, PNG, JPG, ...)](#image-files-bmp-png-jpg-)
  - [Packet Captures](#packet-captures)
    - [DNS Packets](#dns-packets)
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

## Disk Images

Open the image in Autopsy and then go through it. Try global string searches in volumes, and file name searches. Often the `bash_history` file contains valuable info as to what was last done on the machine.

Also, do a search for `.txt` files. They often cont

## Exotic Files

There might be unconventional files provided at times, such as powerpoint files (`.ppt`). These are usually ZIP archives and can be unzipped to reveal usual files and data.

For an exact reference, google the file extension to learn more about the file format.

## Image Files (BMP, PNG, JPG, ...)

Image files almost always require some sort of steganalysis. When such files are received, use `exiftool` to get information about them. Often, PNGs will have extra data appended after the `IEND` chunk (after image end).

A tool that can be used for steganalysis is `zsteg`. Use the command `zsteg -a <file-name>` to get every possible extraction applied to the file. Moreover, `zsteg` will also report the byte offset in a PNG should extra data be appended which then can be extracted using `dd`.

Also, `steghide` and `stegseek` may be used, esp. in case some passphrase is available or if `zsteg` fails. Try `stegseek --seed <file-name>` to check if any one of $2^{32}$ possible seeds were used. This can help to determine if `steghide` was used to hide data.

An important note in bitmap (BMP) files is that they may have mangled header information, such as incorrect height or width. Use `hexedit` to increase the heights and widths just to check if any parts of the image were hidden from view. An online reference for the BMP format can be useful for this: [https://en.wikipedia.org/wiki/BMP_file_format#Bitmap_file_header](https://en.wikipedia.org/wiki/BMP_file_format#Bitmap_file_header).

In image files, if the above techniques fail, try editing the image itself. Try changing the bit depth and similar things (black and white to RGB and vice versa).

Also, `stegsolve` can be used to view various planes of images and with various color maps. It can also extract individual bits of data from pixels. Use [this](https://github.com/zardus/ctf-tools/blob/master/stegsolve/install) link for download instructions, and `java -jar stegsolve.jar` to execute it.

## Packet Captures

Open them up in wireshark. Use `Export Objects` to see if any files can be extracted from them.

### DNS Packets

If there are DNS packets (which there usually are, but pay attention to _how many_ as compared to the total packet capture size), this could be a **DNS data exfiltration attack**. Check for data in domain names, such as `<data string>.example.com`.

## Random Looking File/Binary Data

Sometimes weird files may be extracted/received that have no extension or magic bytes in the header. These might be ZIP archives. Try to unzip them.

Binary files can be viewed using `xxd`. Try `xxd -g 1 <file-name> | less` or `xxd -R always -g 1 <file-name> | less -R` if the terminal supports 8-bit color display to view them.

## Text Data - ASCII

If we have ascii text data, it might be [caesar ciphered](https://cryptii.com/pipes/caesar-cipher) or [base64 encoded](https://www.base64decode.org/). A give away of base64 is `=` signs at the end.

> All base64 strings' lengths need to be a multiple of 3. So, for some possible base64 encoded strings, we need to append `=`'s or prepend a dummy character such as `a` to get the decoding right.
