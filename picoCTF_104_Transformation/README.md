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
