# How the Web Works

## Learning Goals

- Describe the components of a web application framework.
- Manipulate and test the structure of a request object.

***

## Key Vocab

- **Web Framework**: software that is designed to support the development of
  web applications. Web frameworks provide built-in tools for generating web
  servers, turning Python objects into HTML, and more.
- **Extension**: a package or module that adds functionality to a Flask
  application that it does not have by default.
- **Request**: an attempt by one machine to contact another over the internet.
- **Client**: an application or machine that accesses services being provided
  by a server through the internet.
- **Web Server**: a combination of software and hardware that uses Hypertext
  Transfer Protocol (HTTP) and other protocols to respond to requests made
  over the internet.
- **Web Server Gateway Interface (WSGI)**: an interface between web servers
  and applications.
- **Template Engine**: software that takes in strings with tokenized
  values, replacing the tokens with their values as output in a web browser.

***

## Introduction

How many times a day do you use the internet? How many times do you load a
different web page? Think about how many times you do this in a year! As a user,
all you really need to know is the URL to navigate to. You don't need to concern
yourself with what's going on behind the scenes. But if you want to be a web
developer, it's important to have some understanding of how the web works. From
here on out, you are no longer just a user of the internet. You are a creator of
the web.

***

## Client and Server

So seriously, how does this:

```txt
https://github.com/learn-co-curriculum/python-p4-how-the-web-works
```

Turn into this:

![Github README for this lesson](https://curriculum-content.s3.amazonaws.com/python/how-the-web-works-screenshot.png
"README screenshot")

The internet operates based on conversations between the client (more familiarly
known as the browser) and the server (the code running the website you're
trying to load). By typing in that URL into your browser, you (the client) are
_requesting_ a web page. The server then receives the request, processes it, and
sends a _response_. Your browser receives that response and shows it to you.

The simplest kind of websites are known as [**static** websites][static web page],
which typically means sites that store all their content in pre-built HTML files
that are saved to the file system and sent back when a client makes a request for
that specific file.

Static websites are still quite common on the web, but there's also a large portion
of the web that is [**dynamic**][dynamic web page]. With dynamic pages, the content
returned from an HTTP request isn't derived from just an HTML file, but instead is
processed by some code running on the server before it's sent back to the client.

[static web page]: https://en.wikipedia.org/wiki/Static_web_page
[dynamic web page]: https://en.wikipedia.org/wiki/Dynamic_web_page

These are the fundamentals of the web. Browsers send requests, and servers send
responses. Until today, you have always been a client. Moving forward, you will
be building the server.

When working on the server, our goal is always the same three steps:

- Process a request from a client.
- Create a response.
- Send the response to the client.

We will be writing our servers using Python and Flask. But your browser doesn't
know, nor does it care, what server it talks to. How does that work? How can a
server that was written 15 years ago still work with a browser written 15
months (or even _days_) ago?

In addition, you can use multiple clients! You can use Chrome, Safari, Firefox,
Edge, and many others. All of those browsers are able to talk to the same
servers. Let's take a closer look at how this occurs.

***

## HTTP Overview

Communication between different clients and different servers is only possible
because the way browsers and servers talk is controlled by a contract, or
_protocol_. Specifically, it is a protocol created by
[Tim Berners-Lee][sir tim] called **Hyper Text Transfer Protocol**, or HTTP.
Your server will receive requests from the browser that follow HTTP. It then
responds with an HTTP response that all browsers are able to parse.

HTTP is the "language" browsers speak. Every time you load a web page, you are
making an HTTP **request** to the site's server, and the server sends back an
HTTP **response**. When you use `fetch` in JavaScript, you are also making an
HTTP request.

In the example above, the client is making an **HTTP GET request** to GitHub's
server. GitHub's server then sends back a response and the client renders the
page in the browser.

![computer server](https://curriculum-content.s3.amazonaws.com/how-the-web-works/Image_17_ComputerServer.png)

## Requests

### URL

When you make a request on the web, how do you know where to send it? This is
done through **Uniform Resource Locators**, or URLs. You may have also heard
these addresses referred to as URIs (Uniform Resource Identifiers). Both are
fine. Let's look at the URL we used up top:

```txt
https://github.com/learn-co-curriculum/phase-3-how-the-web-works-readme
```

This URL is broken into three parts:

- `https` - the protocol
- `github.com` - the domain name
- `/learn-co-curriculum/phase-3-how-the-web-works-readme` - the path

The **protocol** is the format we're using to send our request. There are
several different types of internet protocols (SMTP for emails, HTTPS for secure
requests, FTP for file transfers). To load a website, we use HTTP or HTTPS.

The **domain name** is a string of characters that identifies the unique location
of the web server that hosts that particular website. This will be things like
`youtube.com` and `google.com`.

The **path** is the particular part of the website we want to load. GitHub has
millions and millions of users and repositories, so we need to identify the
specific resource we want using the path:
`/learn-co-curriculum/phase-3-how-the-web-works-readme`.

For an analogy for how a URL works, think about an apartment building. The
**domain** is the entire building. Within that building, though, there are
hundreds of apartments. We use the specific **path** (also called a resource) to
indicate that we care about apartment 4E. The numbering/lettering system is
different for every apartment building, just as the resources are laid out a bit
differently for every website. For example, if we search for "URI" using Google,
the path looks like this: `https://www.google.com/search?q=URI`. If we use
Facebook to execute the same search, it looks like this:
`https://www.facebook.com/search/top/?q=uri`.

You can learn more about the [anatomy of a URL from MDN][url anatomy].

## The History of Flask

Flask was originally developed by [Armin Ronacher][armron] as an April Fool's
joke in 2010. His goal was to make the smallest viable web framework and pitch
it for use in production code. He leveraged some of his other projects in the
process: [Werkzeug][werk] (German for "work stuff") as an interface between the
application and server, [Jinja][jinja] to turn Python code into HTML, and now
[Click][click], a CLI building tool that we mentioned at the end of Phase 3.

Competing with the well-established and generally beloved Django, he felt that
his proposal would be met with a laugh. After all, Flask didn't do very much.
All of the source code fit comfortably into one file! Much to Ronacher's
surprise, people loved Flask and began submitting hundreds of pull requests on
the repo, suggesting changes to expand its core functionality and compatibility
with different styles of coding.

Ronacher couldn't handle all of these requests himself, so he created [the
Pallets Projects][pp] as a central location for Flask and his other projects.
If you visit the homepage, you'll notice that the docs for Werkzeug, Jinja, and
Click are available right there. This might be a useful page to bookmark, as
most of the important documentation for Phase 4 is right there!

Because it is useful for small and large projects and a wide variety of tasks,
Flask is now the most used Python web framework: It is used at Netflix, Reddit,
Airbnb, Lyft, Uber, and Mozilla, among many, many other companies. Flask isn't
the perfect tool for every task, but we will explore several common use cases
and introduce you to many generalizable key concepts in full-stack web
development.

***

## What to Look Forward to in Phase 4

In Phase 4, we will cover a number of topics in web development:

- Core Components of Python Web Applications
- Web Scraping
- Application Programming Interfaces (APIs)
- Retrieving Data from APIs
- Building APIs with Flask
- Restorative State Transfer (REST)
- Forms and Validations
- Client-Server Communication
- Serialization
- Full-Stack Development with Flask and React
- Deploying a Web Application

Coming out of Phase 4, you will know how to build databases, Flask applications,
and React frontends. This will give you all the tools you need to get started
on your capstone project, as well as any other projects you might have in mind.

Happy coding!

## Resources

- [Flask Documentation][flask]
- [Armin Ronacher][armron]
- [Werkzeug Documentation][werk]
- [Jinja Documentation][jinja]
- [Click Documentation][click]
- [The Pallets Projects][pp]

[flask]: (https://flask.palletsprojects.com/en/2.2.x/)
[armron]: (https://lucumr.pocoo.org/)
[werk]: (https://palletsprojects.com/p/werkzeug/)
[jinja]: (https://palletsprojects.com/p/jinja/)
[click]: (https://palletsprojects.com/p/click/)
[pp]: (https://palletsprojects.com/)
