# Torrent Analyze

This CTF is available [here](https://play.picoctf.org/practice/challenge/311?category=4&page=1&solved=1).

It gives us a pcap and asks us to find a file downloaded using torrent. It also sayd that the flag is of the form `picoCTF{filename}`.

---

I've begun to analyse the pcap. I found several BT-DHT protocol packets, representing connection establishment in the network, but I'm now looking for the packets that actually contain the data, as it is possible that the file name is present in plain text.

---

According to chatgpt, the first task should be to locate the associated `.torrent` file. I'll see if I can extract it.

It seems that we are after the infohash: `17c1e42e811a83f12c697c21bed9c72b5cb3000d`.
