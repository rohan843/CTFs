# CTF Strategies

Here, various strategies that can be followed in CTFs are provided. Each heading and sub-text provides a situation where we might be (such as having an ASCII encoded text file) and then some things that can be done at that point.

The headings will be alphabetical.

## Contents

- [CTF Strategies](#ctf-strategies)
  - [Contents](#contents)
  - [Exotic Files](#exotic-files)
  - [Image Files (BMP, PNG, JPG, ...)](#image-files-bmp-png-jpg-)
  - [Text Data - ASCII](#text-data---ascii)

## Exotic Files

There might be unconventional files provided at times, such as powerpoint files (`.ppt`). These are usually ZIP archives and can be unzipped to reveal usual files and data.

For an exact reference, google the file extension to learn more about the file format.

## Image Files (BMP, PNG, JPG, ...)

Image files almost always require some sort of steganalysis.

## Text Data - ASCII

If we have ascii text data, it might be [caesar ciphered](https://cryptii.com/pipes/caesar-cipher) or [base64 encoded](https://www.base64decode.org/). A give away of base64 is `=` signs at the end.
