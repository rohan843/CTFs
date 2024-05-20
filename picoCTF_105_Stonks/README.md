# Stonks

This challenge is availabe [here](https://play.picoctf.org/practice/challenge/105?page=1&solved=1).

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
