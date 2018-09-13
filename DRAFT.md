![](https://cdn-images-1.medium.com/max/2000/1*u85ztZQtwroYTMkvPLU90A.png)

### The Definitive Guide to Templating

A Template is an HTML document that has some structure, markup and style, which can
be used as a common starting point for an application. In a web application,
there’s usually some recurrent formatting, styling and JavaScript which is shared
across multiple pages. These can include markup like the title and body tag, or common
styles and CSS, or even scripts for executing app logic.

If you’re a web developer who has worked with HTML5, CSS and JavaScript before, you
most probably have heard of templates and template engines. At some point you might
have also encountered different template engines, such as —

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
Today, a web app can have multiple different views on the front-end — each of
these views being drastically different from one another, while also having some
common resemblance in structure. A different view of the app is displayed on the
browser, based on a bunch of parameters. 

For example, some of the parameters for a social networking site like Facebook
could be —

* The URL of the page
* The user that’s using the page
* IP address or location
* Whether the user is logged in, or not.
* People, pages or groups that the user has subscribed to.

Based on these parameters, what John sees in his browser could very well be
different from what Jane sees, for the same website. How does this happen?
Through the use of template engines!

#### A template engine is a special part of your application server that lets you work with templates, and dynamically apply different kinds of customization based on the requests that the server gets.

<br> 

The concept of templating can be applied on both client-side as well as
server-side. Client-side frameworks like AngularJS, ReactJS or VueJS also have their own
templating and rendering logic. But typically, when we speak about template
engines, we’re usually talking about templating on the **server-side**, for
reasons outlined in the above example.

The other significant advantage of using templating is **productivity**. Here’s how you
can be much more productive —

* In bigger projects, separation of concerns become a big problem, and so it’s
very important that you keep your view logic separate from the business logic.
Using templating helps you keep your code organized.
* Keeping the markup code completely separate from the app code means that you can
get more than one person, or a team, to work on the same project. For example,
someone great at front-end development will be able to focus and work on just
building the views and the UI, while someone great at JavaScript will be able to
focus on the business logic. Thus, it encourages teamwork
* It helps you stick with the DRY rule — that is, Don’t Repeat Yourself. By using
templates, you can be more productive.

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

### Let’s get started!

While working with template engines, you’re going to encounter lots of
terminologies and features. It’s important to know what these concepts are and
why are they important so that you’ll understand when used in the context of templating.

### Templating Terminologies

* Expressions and Interpolation
* Delimiters
* Regexes
* Helpers
* Escaping 
* Tokenizing

#### Expressions and Interpolation

An expression is a basic unit of a template. Here’s an example —

    <h4> Hello {{ username }} </h4>

Here, *username* is a variable and is enclosed within a pair of delimiters `{{` and `}}`.
Loosely translated, it means — **replace the word username with whatever value it contains**. This process is called **interpolation**.

Expressions can contain simple valid JavaScript variables, which act like placeholders. 
You can replace this placeholder with whatever string or text you like! 
They can also contain more complex programming constructs, like conditionals and loops.

So in the above example — if you wanted to display a text called *Hello Jon*,
all you need to do is tell the template engine that *username= “Jon”*. The
template engine would then find all occurrences of the variable *username* in
the template, and replace it with *Jon* so that the output would be `<h4> Hello Jon </h4>`.

#### Delimiters

A delimiter defines the scope of a template expression. One commonly used
delimiter is `{{` and `}}`, which is used by template engines like Handlebars. Other
template engines like UnderscoreJS, use the delimiters  `<%=` and `%>`. Delimiters are how the
engine understands that the text between them is an *expression* and it needs to
be evaluated.

#### Regexes

How does the template engine manage to find, evaluate and replace these
expressions with actual data values? You probably might have guessed it right
—through the use of Regexes! 

A **regular expression** is a formula consisting of a sequence of characters,
that allows you to define a search pattern. To know more about them, refer this
[guide](https://guide.freecodecamp.org/javascript/regular-expressions-reference/).

> Bonus stuff: If your project requires regexes, you’ll be interested in
> this super-cool, super-fast library: [Micromatch](https://github.com/micromatch/micromatch)

#### Helpers

Helpers are functions that help you create highly reusable and customizable
expressions, which you can use in very specific scenarios. It can even contain
math expressions, like —

    function fahrenheitToCelsius(temp) {
        return (temp-32) * 5 / 9
    }

Then you could do this —

    <p> The temperature of the Sun's surface is {{fahrenheitToCelsius(9,941)}}ºC </p>

It'll give this output —

    <p> The temperature of the Sun's surface is 5505ºC </p>
    
> Bonus tip: [Handlebars Helpers](https://medium.com/r/?url=https%3A%2F%2Fgithub.com%2Fhelpers%2Fhandlebars-helpers) is a neat little library that lets you use helper functions.
> It has a lot of utilites and support for array methods, regexes, pattern matching and collections

### Templating Concepts

* Partials
* Front Matter
* …

#### Partials

Partials are smaller, re-usable components of a template. Commonly, elements like the head, header, or footer are used across many templates. We can create separate template partials for each of these elements so that we can re-use them across multiple pages.

You can also write common JavaScript code as a separate template partial, since *script* tags are also elements!

Here’s an example — 

    <!-- About Page -->
    <!DOCTYPE html>
    <html lang=”en”>

    {{ partial “head” . }}

    <body>
        {{ partial “header” . }}

        <h4> Welcome to my blog! </h4>

        {{ partial “footer” . }}

        {{ partial “scripts” . }}

    </body>
    </html>

Now, you can create separate partials for all them — 

    <!-- head partial -->
    <head>
        <meta http-equiv=”Content-Type” content=”text/html; charset=UTF-8" />
     
        <link href=”
    " rel=”stylesheet”>
        <title>Booleanhunter’s Blog </title>

    </head>

<br> 

    <!-- header partial -->
    <div class="navbar-fixed">
        <nav class="blue">
            <a href="https://ashwinhariharan.xyz">Booleanhunter's Blog </a>
        </nav>
    </div>

<br> 

    <!-- footer partial -->
    <footer>
        <div class="footer-copyright">
            <div>
                <span class="grey-text">© 2018 booleanhunter, All rights reserved.
                </span>
            </div>
        </div>

    </footer>

Just like the about page, you can re-use these partials in any other page you
want. For example — on a feed page, on a portfolio page, and anything else.

**What’s the advantage of using partials?**

* Using partials helps you create changes that reflect site-wide. For example, if you’d like for the site’s title to be changed, you’d no longer have to edit the title tag across multiple pages. Just editing the title in the *head* partial, will have the change reflected on any template that uses this partial.
* Since partials are part of templates, they have the same advantages of templates too — generating dynamic content based on different conditions, separation of concerns and so on.
* Partials in turn, can have other partials. This allows you to control the level of re-usability/abstraction you need.

#### Front Matter

Front Matter mostly appears in the context of static site generators (which in turn use templating engines). They are templating variables which hold static information. 

You can use them to hold information like the site’s name, footers, contact information, cover image, site’s home URL, or even copyright clauses. You can define and set these variables in a variety of formats, like JSON, YAML or TOML.

You can later include front-matter in your content -  and during compilation, the site generator will replace them with the actual values.

<br>
*****

### FAQ

#### #Q1: When should we use client-side rendering versus server-side rendering?

