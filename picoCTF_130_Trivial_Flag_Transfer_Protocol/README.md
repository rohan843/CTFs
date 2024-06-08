# Trivial Falg Transfer Protocol

This is the last CTF in the picoCTF Forensics playlist, available [here](https://play.picoctf.org/playlists/16?m=130). It gives us a packet capture file called `tftp.pcapng`. I am opening this file via wireshark.

---

On a first glance, this capture contains information of 152413 packets. Almost all of these packets are of a protocol called **TFTP** (trivial file transfer protocol). I've not used this before, so I'll look up its format.

Other than TFTP, there are a few ARP and SSDP packets, small in number (tot. 18) to be manually checked.

I did not find any useful information in the non TFTP packets.

---

I have now studied the TFPT protocol to some extent from [wikipedia](https://en.wikipedia.org/wiki/Trivial_File_Transfer_Protocol). It is a basic version of FTP. It only supports reading a remote file and writing to a remote file, without any authentication stuff whatsoever. It works on UDP.

This is good for my purposes here, as there is very less complexity.

---

I filtered out the non - TFTP packets, and judging by the first packet's body:

![TFTP Headers of the first TFTP packet](./tftp_packet_1.png)

It seems that this `instructions.txt` file is what I'm after. Now to figure out a way to extract it. At this point, I think that the contents of the file are in the UDP stream of this packet.

---

The packet says that the `octet` type of transfer was performed. According to wikipedia:

> "Octet allows for the transfer of arbitrary raw 8-bit bytes, with the received file resulting byte-per-byte identical to the one sent. More correctly, if a host receives an octet file and then returns it, the returned file must be identical to the original."

This means I need to extract the bytes and re-assemble them together into the resultant file.

---

Ok, I have now used the _File -> Export Objects -> TFTP_ option from the wireshark menu, apparently there were quite a few files in the transfer:

![The files extracted from the packet capture](./files_in_capture.png)

---

There were 3 bitmap pictures in the transfer, I viewed them normally. They seem to be normal pictures of mountains and scenery. I will perform usual steganalysis on them.

---

I used `steghide` to try and extract information from the images, but due to no passphrase, none was extracted.

I have 2 text files `instructions.txt` and `plan`. They seem to have gibberish, but maybe a caesar cipher is in place there.

---

Ok, some progress - a rotation of 13 worked to decrypt the caesar cipher on `instructions.txt`. It seems to point us to the file `plan`. I'll try the same.

---

Ok, the plan also got decrypted similarly. It seems that the flag is in the photos and that the file `program.deb` is key to accessing it.

---

I've been reading about `.deb` files. They are debian package files that can be installed. I am also looking into the `dpkg` command to manipulate these files.

---

Ok, so the `program.deb` just turned out to be `steghide`. I unpacked it and used it but still, no passphrase is available.

---

Using `stegseek` I've managed to ascertain that the file `picture2.bmp` contains some hidden data based on the fact that it was the only file in which a seed was found. The encryption algo is what I think DES-3, so without the password its pretty futile but I'm trying to figure out if there's any way to extract the encrypted data.

---

Now, I finally have found the flag. For the passphrase, I had to refer to [this](https://medium.com/@quackquackquack/picoctf-trivial-flag-transfer-protocol-writeup-20c5d2d0dfdf) article. Turns out the passphrase was provided to us all along!
