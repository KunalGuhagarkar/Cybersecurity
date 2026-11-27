# Localhost

**YouTube:** [What is localhost? Simple guide (2026)](https://www.youtube.com/watch?v=m98GX51T5dI)

**Resources:** [What is Localhost? Local Host IP Address Explained](https://www.freecodecamp.org/news/what-is-localhost/)

## What is Localhost?

In computer networking, host means a “server”. Just like you can put a website on the internet by hosting it on a server, you can make your own computer that server. This connection is called loopback. The IP address for that loopback is 127.0.0.1.

If you’ve served a website on your computer so you can test it without connecting to the internet, what you’re dealing with is a localhost.

So, by definition, **localhost is the computer or hostname currently making a request to itself.** In this case, the computer is also the virtual server.

## What is the IP Address 127.0.0.1?

If you type localhost to your browser’s address bar, it transforms to the IP address 127.0.0.1.

This 127.0.0.1 IP address is reserved for local servers on computers, so you will never find another IP address that starts with 127.

## But localhost: what? Or 127.0.0.1: what?

Unlike HTTP and HTTPS which are protocols, localhost is a hostname. Remember that the website domain name is what follows the http or https, for example, https://www.google.com/ and https://www.freecodecamp.org/. So, something has to follow localhost: and 127.0.0.1:. That thing is the port number.

For example, in an Express app, that port number is the port variable you set. Something like this:

``` js
    const port = 4000;
```

So if you type localhost:4000 in the browser address bar and hit ENTER, the web application you’re currently making will be served to you.

Also, if you type 127.0.0.1:4000, you will get the same response

