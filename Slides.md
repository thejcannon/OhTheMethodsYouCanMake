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

---

<!--

Thank you those here and watching online
For allowing me to take up a slice of your time
To share with you a story that's anything but tragic
Of how I learned to use Python's _good_ magic

There are many methods your types can define
That get called by Python: library and runtime
Which make _your_ objects much more expressive
And make _your_ code look really impressive

But beware, as I recant this story to you
Also take the advice that is given too
This magic is good, so good you see
It really should be used sparingly
A pinch here, a smidge there, use only what you need
and never forget "The Zen of Python" - PEP 20

My name is Josh, A Build Engineer by day
Who loves Python and Open-Source, by the way
And anything that makes code easier to read
So should we get started? I think so! Indeed!

---

So...
In my journey through Holland, between hither and yon
I stopped at a tower and I couldn't go on
The tower itself was tall, curvy, and twisty
And the air around it was sweet and misty

A sign hung above a door, held on by some stakes
"The Sanctum Serpentine" with a drawing of two snakes
I went inside where there was a very large plaque
with names with two underscores at the front and the back
The plaque read "The Dunders", I grabbed a quick picture
of all of the Dunders etched into scripture

At that moment a snake slithered up and hissed "How do you do"
"I'm Monty", he smiled, "I'll teach them to you".
And I with my wits, did not know what to do
What would _you_ do if in that tower was you?

So I said "umm sure, I do love me some learning"
and the names on the plaque on that moment started burning
The snake hissed "Most Exccelent" and slithered upstairs
and I followed him, the expert in magic affairs

---

He said "let us start with `__init__`"
I smirked and I boasted, "yeah I've heard of it"
"I'd hoped that what you'd teach me would make me much wiser
So let us skip past an object's _initializer_"

"Yes, everyone's seen it, its usually the first magic you've used
But where did `self` come from?
See now you're confused"

And I wondered, and I stood, and a thought came to me:
"Where _did_ it come from? How was it made to be?
It's already a new instance of my class' type
but blank, only with my class' archetype"

"Come" hissed the snake, up to level two,
so I may show you `__new__`.

I did, and I was met with this signature on the wall,
the most magical method, the magicallest of them all.
It _constructs_ the new instance, and returns it you see
that is how the object has come to be.

Yet there's more the this story than the object's existence,
that hinders on the type hierarchy of the new instance,
if its type matches the class with this `__new__` _in it_,
then the runtime it calls the type's `__init__`.

Otherwise, if the object isn't related to your class
nothing more is done, and to the caller it is passed.
Therefore you can return anything from `__new__`,
but what should be returned is up to you

As an example of this power found in the standard library
is `pathlib.Path`, whose `__new__` is "the cherry".
The value given back to you when you construct it
depends on your platform. Neat, you must admit

--

The opposite of `__new__` is not as exciting when employed,
`__del__` is called right before an object is destroyed.
A good time to release acquired resources,
like locks or descriptors, or all-the-kings-horses.

---

Now, while we're on the subject of object customization,
lets go over magic methods of attribute relation.
The snake then slithered up the tower to be on level three,
and I followed after him, you see.

Starting with `__getattr__`, you might've used it
It synthesizes attributes that don't exist.
It's called when the default attribute access failed,
The attribute name simply just wasn't detailed.
Your class gets a chance to pretend it exists
However, on your object, the attribute doesn't persist.

It has an alter-ego, named `__getattribute__`,
its called unconditionally for attributes, "the brute".
It gets called for names both existing and not,
but beware, infinite recursion is easily got.





...

So when you use them, do so with great care and tact
And remember that Programming's a balancing axt

-->
