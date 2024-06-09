# MacroHard WeakEdge

This CTF is available [here](https://play.picoctf.org/practice/challenge/130?category=4&page=1&solved=1).

We are given a Macro enabled PowerPoint presentation (`.pptm`) and are asked to find the flag in it. I'm not very sure of what macros are, but assumming they are executable commands, there is a slight possibility that should the ppt be opened and macros executed, they will delete the flag. I'm on Kali Linux right now, so I'll try using google slides online to open the ppt, preferably with macros disabled.

---

As a pre-check, I tried opening the ppt in MS Powerpoint, but it said that the format of the file was incorrect and that auto repair could only be done if the file is trusted. I have cancelled that for now. I'm trying to convert the ppt into pdf to view the contents, if the bad format glitch can be taken care of.

---

I converted the document to pdf using cloudconvert, but it was only a pdf document with 57 pages (slides) and the only visible text was on the first slide, that said `Forensics is fun`.
