# Operation Orchid

This CTF is available [here](https://play.picoctf.org/practice/challenge/285?category=4&page=1&solved=1).

It gives us a disk image and asks to find a flag.

The image was a `gz` archive, so I have deflated it using `gzip`. I'll run autopsy and open the image there.

---

By browsing the partitions and performing keyword searches for `flag` among other strings, I got a file that seems to contain the flag, but its been encoded using openssl. I'll see more about the decoding process and proceed.

---

I found the bash history that displays the exact way someone tried to encode the flag. It even shows the encryption key used. I'll proceed to decrypt the flag accordingly.
