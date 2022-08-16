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

![Github Readme](https://curriculum-content.s3.amazonaws.com/phase-3/how-the-web-works-readme/github-readme.png)

## The History of Flask

![Flask logo with text: "web development, one drop at a time"](https://curriculum-content.s3.amazonaws.com/python/1200px-Flask_logo.png "flask logo")

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
