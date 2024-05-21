# GET aHEAD

This CTF is available [here](https://play.picoctf.org/practice/challenge/132?page=1&solved=1).

It gives us a link: `http://mercury.picoctf.net:15931/` and asks us to find the flag on this server.

---

I have `curl`ed the HTML response from the server into a file `red.html`. On Firefox, it simply displays a webpage with a red background (hence the name of the file) with 2 buttons that change the color of the page to blue or to red.

---

There seems no JS involved whatsoever. There was an `action` attribute in a `form` element with the value `index.php`. There was a `GET` request and another `POST` request made with this same `action` value.

This suggests there is a PHP file `index.php` at the server. Possibly the one that contains the flag.

---

I made a `GET` request to the `index.php` endpoint (`curl http://mercury.picoctf.net:15931/index.php`) but got the same HTML back. Based on the [last](../picoCTF_105_Stonks/) CTF I did, I've learned that focussing on user inputs rather than outputs is more useful for exploitation. Therefore, I'll focus on the `POST` request to this endpoint now.

There is no "input" as such though, as the only entity in the form is the button, which may or may not have been pressed (it won't be clicked if I use `curl`).

---

I have made a POST request, but have received the same HTML, only with `blue` as the background color. As a precaution, I checked the response headers. There was only one - the `Content-type`, with the usual data.
