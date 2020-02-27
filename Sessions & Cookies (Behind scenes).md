cookies have to turned on in order for sessions to work?

On most cases, yes. You can, however, set it so that session IDs are transmitted via GET variable 
(which would mean that the session_id would need to be appended to every page (hello.php?sid=cbe709ac7bed98f7ecb89713) 

Cookies
Cookies are small bits of data, (maximum of 4KB long), which hold data in a key=value pairs:

name=value; name2=value2
These are set either by JavaScript, or via the server using an HTTP header.

Cookies have an expiry datetime set, example using HTTP headers:

Set-Cookie: name2=value2; Expires=Wed, 19 Jun 2021 10:18:14 GMT
Which would cause the browser to set a cookie named name2 with a value of value2, which would expire in about 9 years.

Cookies are considered highly insecure because the user can easily manipulate their content. That's why you should always validate cookie data. Don't assume what you get from a cookie is necessarily what you expect.

Cookies are usually used to preserve login state, where a username and a special hash are sent from the browser, and the server checks them against the database to approve access.

Cookies are also often used in sessions creation.

Sessions
Sessions are slightly different. Each user gets a session ID, which is sent back to the server for validation either by cookie or by GET variable.

Sessions are usually short-lived, which makes them ideal in saving temporary state between applications. Sessions also expire once the user closes the browser.

Sessions are considered more secure than cookies because the variables themselves are kept on the server. Here's how it works:

Server opens a session (sets a cookie via HTTP header)
Server sets a session variable.
Client changes page
Client sends all cookies, along with the session ID from step 1.
Server reads session ID from cookie.
Server matches session ID from a list in a database (or memory etc).
Server finds a match, reads variables which are now available on $_SESSION superglobal.
If PHP does not find a match, it will start a new session, and repeat the steps from 1-7.

You can store sensitive information on a session because it is kept on the server, but be aware that the session ID can still be stolen if the user, let's say, logged in over an insecure WiFi. (An attacker can sniff the cookies, and set it as its own, he won't see the variables themselves, but the server will identify the attacker as the user).

