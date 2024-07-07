# WPA-ing Out

This CTF is available [here](https://play.picoctf.org/practice/challenge/237?category=4&page=1&solved=1).

It gives us a pcap and asks us to find a password, that it says is also present in the `rockyou.txt` word list.

---

The pcap contains a lot of `802.11` packets, but nothing seems to be at or above the internet layer. I did find an SSID `Gone_Surfing`. This suggests that perhaps the password we are looking for is the wifi password.
