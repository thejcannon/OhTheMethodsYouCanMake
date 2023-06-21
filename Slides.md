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
The snake hissed "Most Excellent" and slithered upstairs
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
(Emulating Attributes)

Now, while we're on the subject of object customization,
lets go over magic methods for attribute emulation.
The snake then slithered up the tower to be on level three,
and I followed after him, you see.

Let's see now `__getattr__`, Monty then hissed
It synthesizes attributes that don't exist.
It's called when default attribute access fails,
The attribute simply wasn't in the details.
Your class gets a chance to pretend it existed
However, on your object, the attribute isn't persisted.

It has an alter-ego, named `__getattribute__`, you see
which is called for all access, _unconditionally_
It gets called for names both existing and not,
but beware, infinite recursion is easily got.

Now on the other side, `__setattr__` is how,
attribute setting, your classes allow.
Again, by default the attribute isn't persisted,
you get to choose whether it becomes listed.
This is also called for all attributes without any condition,
whether is existed or not, without your permission.

The last of the attr methods, people sometimes leave off,
define `__delattr__`, and people might scoff.
As you probably can guess its good for emulation
of the removal of a name from your object's formation.
And just like `__setattr__`'s unfortunate asymmetry,
it gets called unconditionally.

Then, Monty said, well there's `__dir__`.
I mean, you can define it, if you prefer.
It gets called, if its there, by the builtin `dir`,
to return valid attribute names, back to the caller.

And so now you know, the magic incantations
that you can use in certain combinations
to pretend your object has more than it does
for good reasons, or maybe, just because.

However, in our attribute story, there is more.
Monty said before slithering to level 4

---
(Descriptors)

I have 4 methods, I'll teach to you now,
these methods are powerful, you'll see how,
an attribute gets to customize _itself_
instead of sitting static on an object's shelf.

"Descriptors" is the name given to this technique
of attributes themselves, using doublespeak.

First these things work as attributes of the class
(you'll see Django and SQLAlchemy use this en masse)
The descriptor is the attribute, and it gets a say
on how _it_ gets gotted, setted, and deleted, per se

`__get__` is the first of these spells you'll want to perfect
conjuring values for attributes based on the caller's object
(or sometimes the class, as callers sometimes will do,
using class attribute lookup, so support that too).

You've maybe have wondered, and even had a theory,
how SQL ORM's quickly fire off a query,
when you run something like `my_user.amount_in_debt`
the "Column" descriptor is leveraging `__get__`
to run a SQL query, using `my_user`'s ID,
and return to you the value (and maybe cache it, you see)

Just like `__getattr__`, `__get__` has two brothers,
`__set__` and `__delete__` are the others.
They act just like `__get__` in proxying a call,
and can do anything they want, both big and small.

For metaphorical purposes, let's finish our "Column" story,
and see how these methods are very applicatory,
`__set__` gets called for attribute assignment,
A SQL `UPDATE` is likely used for new value enshrinement
And `__delete__` when an attribute is told to go bye-bye
a SQL `DELETE` is likely to go by.

There's one more method, in case you've been counting,
how a descriptor knows its name in its internal accounting
Like how the SQL query knows the right column to use,
`__set_name__` is a part of this too.

At the end of your class definition, you see,
for all of the class attributes that be,
if they define a `__set_name__`,
the attribute's name, Python will disclaim.

And thus the attribute shell game, now comes to a close
the illusions of attributes, we have now exposed
Although more illusions we'll make come alive,
And then Monty slithered up to level 5.

---
(Containers)

On level 5 I listened, to Monty the explainer,
and he told me how to emulate a data container.

Our trio of methods we kept using for attributes,
are also found in a data container's roots.
`__get`-, `set`-, and `del`- have the suffix of `item__`
[[[ talk about semantics? Like IndexError/KeyError ]]]
(this topic was is something that seemed to excite him)

They are given the key (and in one case, the value)
implementing container semantics are then up to you.
As and far as semantics go, there are a few more dunders
you'll want to define, lest you commit several blunders

A quick one that you will define,
is `__len__` which helps Python divine
the length of your container, so when people cal `len`,
Python can return the number back to them.

The second one is `__iter__`, which should return an iterator
over the objects that all live inside your object container,
unless its a mapping then what the iterator sees,
is simply all of the mappings keys.
There's also this trivia, a bit of Python fun,
if your container isn't iterable, set `__iter__` to `None`!

Now, third on our list is named `__contains__`,
to support things like `if "thomas" in all_of_the_trains`.
Although technically, you don't have to define it, Python won't be bitter
Instead it'll test membership first using `__iter__`.
Going over every possible object that your object can contain,
and asking if any of those objects are equal or the same.
But if you also don't define a `__iter__` method,
`__getitem__` is called and repeatedly tested,
using incrementing indexes from 0 until it then gets
an `IndexError` exception or an equal/same object.
So it's best to define it, so you have control,
just how the object membership test will unroll.

And if for optional methods you happen to thirst,
another one available is `__reversed__`.
It returns an iterator for doing backwards iteration,
but only define it, if you beat the default computation,
that Python uses combining `__getitem__` and `__len__`
indexing backwards to 0

_fin_

Or at least we're done with container magic tricks
Follow me upwards to be on level 6

---



...

So when you use them, do so with great care and tact
And remember that Programming's a balancing axt

-->
