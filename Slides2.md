---
marp: true
footer: "#NorthBayPython 2023 - Oh the (Methods) You Can (Make): By Dunder Seuss  - ![w:40 h:20](./images/discord.png) thejcannon#4100"
theme: gaia
class:
  - lead
  - invert
---

<style>
code {
  font-family: courier;
  color: #fff176;
  font-size: 100%;
  background: none;
}
</style>

<!-- _backgroundImage: linear-gradient(to bottom,rgba(0, 0, 0, 0.6),rgba(0, 0, 0, 0.8)), url(./images/background.jpg); -->

# Oh the (Methods) You Can (Make)

By Dunder Seuss

# About the author

...

<!--
Josh Cannon, aka "Dunder Seuss" ...

-->

---

<!--
Congratulations!
Today is your day.
You will soon learn you some magic,
the good and proper way.

You've chosen a wise way to spend your precious time
by listening to some crazy loon go on in rhyme
about a list of methods that are nicknamed "the dunders"
and how you'll use them to code great wonders

They start with two underscores, and end with two more
thus "dunder" which is short for "double underscore"

The runtime of Python calls them in many situations
allowing _your_ objects many customizations

You'll learn all about how to emulate a container
and iterators and numbers from a great explainer
Comparisons, callables, and descriptors too,
and how to make attributes appear out of the blue.

You'll learn some new names, and I know you'll learn many
at least one if not two, maybe even up to twenty

By the end you'll know magic, know magic galore
you'll be so full of magic, you'll yell "please sir no more"!

So with great skillful skill, and lots of caffeine
let's start off your learning... with a method you've seen

---

Let's pretend you're new to Python, just for a minute
you'll then learn the first magic: `__init__`
It is almost every object's _initializer_,
allowing you to be an attribute organizer
adding new attributes to your fresh new object.
The most common magic, I truly do suspect.

But,
where did `self` come from?
You'll soon start to wonder

Then you'll learn that its created by just another 'dunder
One that _constructs_ the blank object to give to you
And it's name, you'll soon find, is `__new__`.

It's a special static method you'll maybe define in your class
which returns _some_ object, then onward its passed,
to whom it turns out depends on the returned object's type
if its an instance of your class (including a possible subtype)
"it goes to `__init__`" you'll hear from the scholar
"but otherwise", he'll says, "it's back to the caller"

You'll see this in action, and it'll be more clear-y
by looking for it's use in the standard library
`pathlib.Path` uses this method to help it perform
constructing an object specific to _your_ platform.
The type, as you'll find, has defined `__new__`,
to return a subclass' instance specific to _you_.

Now, with great careful care, and great tactful tact,
you'll see using it is a great balancing act.
A magic with the power to create objects that are new,
is something to avoid misuse of, too.

---

And speaking of balance,
the opposite of `__new__` is not oft employed,
`__del__` is called right before your object is destroyed.
You'll use it to release resources you've acquired
but only if you want, its definition isn't _required_
But if you do write it, heed this warning as well,
you __MUST__ call your `super()`'s `__del__`.

---



-->
