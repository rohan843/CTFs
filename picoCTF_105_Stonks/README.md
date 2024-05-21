# Stonks

This challenge is available [here](https://play.picoctf.org/practice/challenge/105?page=1&solved=1).

It gives us a file called `vuln.c` and a bash command `nc mercury.picoctf.net 33411`.

---

Looking at the code in `vuln.c` and the behaviour of the `nc` command, it seems that the C code is being run at the server.

The code has the following snippet in its `int buy_stonks(Portfolio*)` function:

```c
FILE *f = fopen("api","r");
	if (!f) {
		printf("Flag file not found. Contact an admin.\n");
		exit(1);
	}
```

This suggests that we need access to the contents of the local file `api` as it is being refered to as the "Flag" file in the error message.

---

Accessing the file `api` is turning out to be complex. The following line:

```c
fgets(api_buf, FLAG_BUFFER, f);
```

stores the contents of the file in the local char array `api_buf` (that was dynamically allocated via `malloc`), but `api_buf` is not used anywhere else in the C program. This makes it difficult to access it remotely.

It _is_ possible that the code we are given is not the code actually running, but an older version of it, because of the multiple `TODO`s.

I'll keep trying out ideas here...

---

I was not able to find any clue as to the next steps. Before consulting the hint on picoCTF website, I decided to google _binary exploitation_ (the tag for this problem) and found this website: [https://ctf101.org/](https://ctf101.org/). It might give some useful information.

---

So.. that didn't help much. I have consulted the available hint. The hint is: `Okay, maybe I'd believe you if you find my API key.`

This suggests that the "API Token" that the server asks for (which was as of now ignored in `vuln.c`) is actually used in the code being executed, and it is what will help us get the `api_buf` (somehow).
