![](https://cdn-images-1.medium.com/max/2000/1*u85ztZQtwroYTMkvPLU90A.png)

### The Definitive Guide to Templating

A Template is an HTML document that has some structure, markup and style, which
can be used as a common starting point for an application. In a web application,
there’s usually some recurrent formatting, styling and JavaScript which is
shared across multiple pages. These can include markup like the title and body
tag, or common styles and CSS, or even scripts for executing app logic.

If you’re a web developer who has worked with HTML5, CSS and JavaScript before,
you most probably have heard of templates and template engines. At some point
you might have also encountered different template engines, such as — 

* [Mustache](https://mustache.github.io/)
* [Handlebars](http://handlebarsjs.com/)
* [Underscore](https://underscorejs.org/)
* [EmbeddedJS](http://www.embeddedjs.com/), or EJS
* [Jade](http://jade-lang.com/)
* [doT](http://olado.github.io/doT/index.html)
* [Pug](https://pugjs.org/api/getting-started.html)

But what do all these template engines have in common? What lies at the heart of
a template engine? And why do we even need them in the first place? Keep
reading!

### Table of Contents

* The need for templates and template engines
* Whom this guide is for
* Common templating terminologies, features and concepts
* Template syntaxes and languages, and how they work
* Template Engines
* Examples and comparisons of different implementations
* Additional resources and projects

### What’s the need for templates and template engines?

To put it simply — 

#### A template allows you to use the same set of presets and formatting for different views of an application, without having to re-create these formats over and over again.

Websites are no longer what they used to be two decades ago. They’ve grown in
complexity, evolving from simple static web pages to complex web applications.
Today, a web app can have multiple different views on the front-end —  each of
these views being drastically different from one another, while also having some
common resemblance in structure. A different view of the app is displayed on the
browser, based on a bunch of parameters. For example, some of the parameters for
a social networking site like Facebook could be — 

* The URL of the page
* The user that’s using the page
* IP address or location
* Whether the user is logged in, or not.
* People, pages or groups that the user has subscribed to.

Based on these parameters, what John sees in his browser could very well be
different from what Jane sees, for the same website. How does this happen?
Through the use of template engines!

#### A template engine is a special part of your application server that lets you work with templates, and dynamically apply different kinds of customisation based on the requests that the server gets.

<br> 

Now that you have understood what it’s all about, it’s time to dig into some
deeper stuff!

### Whom this guide is for: 

Templating is ubiquitously useful across every programming language, for
everything from rendering web pages, to dynamically generating code files for
things like routes and models. Note that this isn’t about Client-side
Templating, which is typically done by front-end JavaScript frameworks like
AngularJS or ReactJS. We will be discussing specifically in the context of
server-side templating, using NodeJS.

By the end of this tutorial, you’ll get a better understanding of what makes up
a template engine, terminology, different engines and how they work, template
syntaxes and features. At the end of this tutorial, you will —

* Understand how templating in NodeJS works
* Get to know templating lifecycle methods
* Build your own engine and integrate it with ExpressJS
* Use a template engine to build a static site generator for your projects!

<br> 

<br> 
