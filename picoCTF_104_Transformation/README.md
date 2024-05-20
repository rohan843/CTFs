# Transformation

This challenge is available [here](https://play.picoctf.org/practice/challenge/104).

It is a reverse engineering challenge. It gives us a text file `enc` with some unicode characters in it.

According to `exiftool`, the following metadata was obtained:

![`exiftool enc`](./exiftool%20enc.png).

This shows us that it is a `utf-8` file.

We are also given this python-ish command:

```python
''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])
```

Looking at this command, it can be assummed that `flag` is the string of text in the file `enc`. There is one problem though - the command when run as-is gives the following error:

```python
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 1, in <listcomp>
ValueError: chr() arg not in range(0x110000)
```

Moreover, even if this error had not come up, there would have been an out-of-bounds access when `i` will become `18`, considering that `len(flag)` is `19` (if we assume that the string in `enc` is the `flag`).

---

Based on all this, and the fact that this was listed under _reverse_ engineering, I'm now considering that maybe `flag` actually refers to the actual flag, and that the contents of `enc` file were generated using the python command.

I will test out this theory by trying to apply the reverse of this command to the string in `enc`.

---

I have further analysed the python command. Assumming it was meant for the actual flag, `flag[i]` refers to some ASCII character, i.e., an 8-bit character. Judging by the left shift operation: `ord(flag[i]) << 8` and the summation operation: `(ord(flag[i]) << 8) + ord(flag[i + 1])`, it seems that I need to look at the 2 lower bytes of each character and ignore the third byte.

---
