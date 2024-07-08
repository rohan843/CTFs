# WPA-ing Out

This CTF is available [here](https://play.picoctf.org/practice/challenge/237?category=4&page=1&solved=1).

It gives us a pcap and asks us to find a password, that it says is also present in the `rockyou.txt` word list.

---

The pcap contains a lot of `802.11` packets, but nothing seems to be at or above the internet layer. I did find an SSID `Gone_Surfing`. This suggests that perhaps the password we are looking for is the wifi password.

---

I analysed the pcap more to find out that the wifi network is an open network, and therefore will not be associated with any password. Based on the number of packets sent by various participants, I have identified one MAC address that had performed the highest number of communications. Its filter is: `wlan.addr==1c:bf:ce:17:b0:be`. I think that it might be sending some data somewhere with some password. There was mention of WPA somewhere, so I'll look into what WPA is.

---

I have found that `WPA-PSK`, which is used by WPA2 is a passkey that is used to secure communications. It makes sense to believe that this might be the passkey we are looking for.

---

I took a look at the hints, and also an online article that pointed me to a tool called `aircrack-ng` which might be helpful.
