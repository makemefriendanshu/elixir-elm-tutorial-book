# Elm Intro

Elm is likely to look and feel a little foreign at first. But don't let that
scare you away, because it's a _very_ strong language that can be _very_ nice
to work with.

The design of Elm allows the language to offer things that many other languages
simply can't. Not only does it enable developers to write code that is free
from errors, but also results in code that is easier to refactor and more
maintainable.

I could honestly go on for months about how great Elm is (and I do that at the
local Elm meetup that I help organize), but let's just dive into some really
basic examples.

## Hello.elm

We can start with a simple "Hello World" example, and it will show how easy it
can be to get Elm up and running. Here's what a simple Elm program (with a
filename of `Hello.elm`) looks like:

```elm
module Hello exposing (..)

import Html


main =
    Html.text "Hello World"
```

On the one hand, the syntax is _really_ concise, and this is a really quick way
to get some text on to a page in your browser (we'll get to that in a second).
But this example is particularly good because it already shows a handful of
things about Elm that might seem unsettling at first. Where are all the
parentheses and curly braces? What's with the odd spacing?

## Elm Syntax

The first line is Elm boilerplate for defining our module. Since this is a
functional language, everything we do is essentially going to be modules and
functions. Functions will be _everything_ to us, and modules will help us
gather and organize all those functions. What we're saying with the first line
of code is that we're creating the `Hello` module, and "exposing" everything
(`..`) from it. So if someone wanted to use our application, they would just
need to import it and they could use any function they'd like.

## Modules, Functions, and Types

Speaking of imports, the next line says `import Html`. This allows us to use
any function from Elm's built-in
[Html library](http://package.elm-lang.org/packages/elm-lang/html/2.0.0/Html).

The function that we're using in this program is the
[`Html.text`](http://package.elm-lang.org/packages/elm-lang/html/2.0.0/Html#text)
function, which takes a single string as an argument. If we take a look at the
documentation for the `text` function, we can see the Elm type syntax:

```elm
text : String -> Html msg
```

That means when we added `Html.text "Hello World"` to our program, the `"Hello
World"` was our only argument. And `Html msg` was the return type. Don't worry
too much about typing yet, but it's helpful to think about a couple of quick
things for now:

- How many arguments does a function take?
- What is the type of each argument?
- What is the type of the return value?

In our case, `text` is the name of the function. Then we use a `:` before the
list of arguments. This function only takes a single argument, and it's a
`String`. Then we use the arrow symbol `->` after the argument. And lastly we
indicate the return type, which is an `Html msg`. The `msg` part isn't
important, and we could've said `Html a`. The important part is that we are
returning some HTML code that we are going to use to display the text on a
page in the browser.

## Main Function

The `main` function is basically the starting point for our application. When
we run it, the Elm runtime is going to look for `main`. But Elm is _way_ more
fun to play with than it is to read about, so let's finally run our example.

Before we can run Elm code, we'll need to install Elm. There are different
ways of doing it, but the easiest way is to use `npm` since most developers
have Node installed already.

```bash
npm install -g elm
```

That should be all you need. It globally installs the `elm` command on your
machine, so you can run it from the command-line. In fact, type `elm` now and
take a look at the output:

```bash
$ elm
Elm Platform 0.18.0 - a way to run all Elm tools

Usage: elm <command> [<args>]

Available commands include:

  make      Compile an Elm file or project into JS or HTML
  package   Manage packages from <http://package.elm-lang.org>
  reactor   Develop with compile-on-refresh and time-travel debugging
  repl      A REPL for running individual expressions

You can learn more about a specific command by running things like:

  elm make --help
  elm package --help
  elm <command> --help

In all these cases we are simply running 'elm-<command>' so if you create an
executable named 'elm-foobar' you will be able to run it as 'elm foobar' as
long as it appears on your PATH.
```

We'll use all these features at some point, but for now let's focus on two of
them. First, we'll use the `package` option we see above to fetch the tools
we'll use.

```bash
$ mkdir elm
$ cd elm
$ elm-package install
```

We're creating an empty `elm` folder, and then when we run `elm-package install`
it's going to create all the files we need:

```bash
$ elm-package install
Some new packages are needed. Here is the upgrade plan.

  Install:
    elm-lang/core 5.1.1
    elm-lang/html 2.0.0
    elm-lang/virtual-dom 2.0.4

Do you approve of this plan? [Y/n] Y
Starting downloads...

  ● elm-lang/virtual-dom 2.0.4
  ● elm-lang/html 2.0.0
  ● elm-lang/core 5.1.1

Packages configured successfully!
```

This is everything we need. Let's create the simple `Hello.elm` file for our
"Hello World" program:

```elm
module Hello exposing (..)

import Html


main =
    Html.text "Hello World"
```

All that's left is to run our program. Elm comes with a utility called
`elm-reactor` that we can use to serve our program locally and then access
it in our browser. Go ahead and run it from the command-line:

```bash
$ elm-reactor
elm-reactor 0.18.0
Listening on http://localhost:8000
```

Now you can visit `http://localhost:8000/` in your browser and see the files
and dependencies for our project. We only have a single Elm file (`Hello.elm`),
so let's click it to compile and see the results.

![elm-reactor](images/elm-intro/elm-reactor.png)

![Elm Hello World Example](images/elm-intro/elm-hello-world.png)

## elm-format

Okay, this is admittedly not the most exciting example. But the good news is
that we have Elm installed and have a simple program up and running.

Let's take a look a couple more simple things with this example that will
make our lives easier.

Before we move any further, definitely take a look at
[`elm-format`](https://github.com/avh4/elm-format). It's a plugin that you can
use for your editor that makes working with Elm much easier. It's particularly
great when you're getting started, because you can type a rough idea of what
you want to do and then immediately know if it's valid code as long as
`elm-format` reformats the code and doesn't mention errors or warnings.

While `elm-format` is not strictly necessary, and you can write good Elm code
without it; it's a very helpful tool that can help you focus on problem-solving
instead of worrying about valid syntax.

## Comments and Type Signatures

Let's go ahead and add a quick comment with the `-- comment` syntax to
indicate the filename at the top:

```elm
-- Hello.elm
module Hello exposing (..)

import Html


main =
    Html.text "Hello World"
```

Next, let's refactor our `import` statement slightly to be more explicit about
which functions we want to import:

```elm
-- Hello.elm
module Hello exposing (..)

import Html exposing (text)


main =
    text "Hello World"
```

...

## Topics

- Syntax Basics
- Piping and Data Transformation
- Pattern Matching
- Maybe and Result
- Elm Architecture

## Building a Static Page

...