# **cookies**
## HTTP cookies
An HTTP cookie (web cookie, browser cookie) is a small piece of data that a server sends to a user's web browser. The browser may store the cookie and send it back to the same server with later requests. Typically, an HTTP cookie is used to tell if two requests come from the same browser—keeping a user logged in, for example. It remembers stateful information for the stateless HTTP protocol.

#### The lifetime of a cookie can be defined in two ways:

Session cookies are deleted when the current session ends. The browser defines when the "current session" ends, and some browsers use session restoring when restarting. This can cause session cookies to last indefinitely.
Permanent cookies are deleted at a date specified by the Expires attribute, or after a period of time specified by the Max-Age attribute.


### Restrict access to cookies
You can ensure that cookies are sent securely and aren't accessed by unintended parties or scripts in one of two ways: with the Secure attribute and the HttpOnly attribute.

A cookie with the Secure attribute is only sent to the server with an encrypted request over the HTTPS protocol. It's never sent with unsecured HTTP (except on localhost), which means man-in-the-middle attackers can't access it easily. Insecure sites (with http: in the URL) can't set cookies with the Secure attribute. However, don't assume that Secure prevents all access to sensitive information in cookies. For example, someone with access to the client's hard disk (or JavaScript if the HttpOnly attribute isn't set) can read and modify the information.

#### Cookie prefixes
Because of the design of the cookie mechanism, a server can't confirm that a cookie was set from a secure origin or even tell where a cookie was originally set.

A vulnerable application on a subdomain can set a cookie with the Domain attribute, which gives access to that cookie on all other subdomains. This mechanism can be abused in a session fixation attack. See session fixation for primary mitigation methods.

As a defense-in-depth measure, however, you can use cookie prefixes to assert specific facts about the cookie. Two prefixes are available: __Host-

### What is a cookie?
Quite simply, a cookie is a small text file that is stored by a browser on the user’s machine. Cookies are plain text; they contain no executable code. A web page or server instructs a browser to store this information and then send it back with each subsequent request based on a set of rules. Web servers can then use this information to identify individual users. Most sites requiring a login will typically set a cookie once your credentials have been verified, and you are then free to navigate to all parts of the site so long as that cookie is present and validated. Once again, the cookie just contains data and isn’t harmful in and of itself.

### Cooke creation
A web server specifies a cookie to be stored by sending an HTTP header called Set-Cookie. The format of the Set-Cookie header is a string as follows (parts in square brackets are optional):

```
Set-Cookie: <em>value</em>[; expires=<em>date</em>][; domain=<em>domain</em>][; path=<em>path</em>][; secure]
```

## Conclusion
There’s a lot to know and understand about cookies in order to use them effectively. It’s truly amazing how a technique created more than ten years ago is still in use in almost the exact same way as it was first implemented. This post is a guide to the basics that everyone should know about cookies in browsers but is not, in any way, a complete reference. Cookies are an important part of the web today and improperly managing them can lead to all kinds of issues from poor user experience to security holes. I hope that this writeup has shed some light on the magic of cookies.


### Cookies
HTTP, the protocol that takes care of the communication between a server and a client on the web, is known as a stateless protocol. In other words, if a user requests two pages on a server, no information will be shared between these two requests automatically. Instead, a developer will have to rely on something called cookies (or sessions - more on those later) to share information between the requests. This is extremely useful in a lot of situations, e.g. to keep a user logged in between several requests etc.

Pretty much all server-side technologies have built-in support for handling cookies and of course the ASP.NET MVC framework does as well. In fact, dealing with cookies is pretty easy, thanks to the functionality found on the HttpContext class. In this article, you'll learn how to set a cookie and then read it again afterwards, so that you will be able to share information about a specific visitor between his/hers requests.

### What is a cookie?
A cookie is basically a physical, plain-text file stored by the client (usually a browser), tied to a specific website. The client will then allow this specific website to read the information stored in this file on subsequent requests, basically allowing the server (or even the client itself) to store information for later use.


### Summary
Thanks to cookies, you can save information about the visitor and retrieve it again on subsequent requests. This is a very important technique, used in a wide range of situations, like keeping the user logged in, tracking their use of your website and much more.
