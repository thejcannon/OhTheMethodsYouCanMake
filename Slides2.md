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
Josh Cannon, aka "Dunder Seuss" has written no books so far, has been on a single podcast, and done
exactly one talk before he decided to write this one.

Josh is a Build Engineer by day,
a maintainer of the Pantsbuild Open Source Build System also by day.
And sometimes participates in other open source projects, Python community discussions,
and conference speaking... also by day.

He's a lover of getting to know enough Python to make expressive, readable, intuitive code, and wrote
this book to teach others of the power and magic that you can bring to your objects to make them
expressive, readable, and intuitive.

-->

---

For Dottie and Teddy

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

And speaking of balance...

the opposite of `__new__` is not oft employed,
`__del__` is called right before your object is destroyed.
You'll use it to release resources you've acquired
but only if you want, its definition isn't _required_
But if you do write it, heed this warning as well,
you __MUST__ call your `super()`'s `__del__`.

---

The next set of magics involve conjuring illusions,
of attributes, giving your callers delusions
that your object has more (or less) than it does
why? friendly interfaces is likely the because.

First on your journey through attribute emulation,
`__getattr__` is the proper incantation
you'll type it out with a flick and a twist
and you'll synthesize attributes that don't exist.
It's called when default attribute access fails,
The attribute simply wasn't in the details.
You'll get a chance to pretend it existed
However, on your object, the attribute isn't persisted.
Now, if you wish to pretend you don't recognize this `name`,
`raise AttributeError` emulates that all the same.

It has an alter-ego, named `__getattribute__`, you'll see
which is called for all access, _unconditionally_
It gets called for names both existing and not,
but beware, infinite recursion is easily got.
So remember when you need to access your attributes inside of this thing,
you wont use `self.`, you'll give your `super()` a ring

To juxtapose "get", `__setattr__` is how,
attribute _setting_, your classes allow.
Again, by default the attribute isn't persisted,
you get to choose whether it becomes listed.
This is also called for all attributes without any condition,
(whether it exists or not) without your permission.

The last of the attr methods, you'll maybe leave off,
define `__delattr__`, and people might scoff.
As you'll probably guess its good for emulation
of the removal of a name from your object's formation.
And just like `__setattr__`'s unfortunate asymmetry,
it gets called for all names, unconditionally.

[[ __dir__?]]

---

You'll then find out soon enough,
that when it comes to illusory stuff
attribute names is just where it starts
there's more you'll learn: another TWO parts
yes, like all good things these magics come in three
in more ways than one, you'll soon see
the first way is the trio of names "get", "set", and "del"
then how they're used for illusions as well

The second in our trio-of-trios, I'll teach to you now,
these methods are so powerful. You'll see how,
an attribute gets to customize _itself_
instead of sitting _static_ on an object's shelf.

"Descriptors" is the name given to this technique
of attributes themselves, using doublespeak.

First these things work as attributes of the class
(you'll see Django and SQLAlchemy use this en masse)
The "descriptor" is the attribute, and it gets a say
on how _it_ gets gotted, setted, and deleted, per se

`__get__` is the first of these spells you'll want to perfect
conjuring values for attributes based on the caller's object
(or sometimes the class, as callers sometimes will do,
using class attribute lookup, so support that too).

You've maybe have wondered, and even had a theory,
how SQL ORM's quickly fire off a query,
when you've run something like `my_user.amount_in_debt`
the "Column" "descriptor" is leveraging `__get__`
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
a SQL `DELETE` you'll likely see fly by.

There's one more method, that plays in the "descriptor" game,
and it's a method that goes by `__set_name__`
our "trio" really is four, oh well, what a shame.

At the end of your class definition, you see,
for all of the class attributes that be,
if they define a `__set_name__`,
the attribute's name, Python will disclaim.

And thus the _attribute_ shell game, now comes to a close
the illusions of _attributes_, we have now exposed
the last trio-of-trios, you'll learn from your trainer,
is emulating items inside of a container

---

You'll see this time our trio's suffix is `item`,
to help quack like containers with things inside 'em

They are given the key (and in one case, the value)
implementing container semantics are then up to you.
As and far as semantics go, there are a few more dunders
you'll want to define, lest you commit several blunders

So although our trio of trios may have come to a close
you'll want to learn the other container methods I suppose.

A quick one that you'll want to define,
is `__len__` which helps Python divine
the length of your container, so when people cal `len`,
Python can return the number back to them.

The second one is `__iter__`, which should return an iterator
over the objects that all live inside your object container,
unless its a mapping then what your caller sees,
is simply all of the mapping's keys.
There's also this trivia, a bit of Python fun,
if your container isn't iterable, set `__iter__` to `None`!

Now, third on our extras is named `__contains__`,
to support things like `if "thomas" in all_of_the_trains`.
Although technically, you don't have to define it, Python won't be bitter
Instead it'll test membership first using `__iter__`.
Going over every possible object that your object can contain,
and asking if any of those objects are equal or the same.
But if you also don't define a `__iter__` method,
`__getitem__` is called and repeatedly tested,
using incrementing indexes from 0 until it then gets
an `IndexError` exception or an equal/same object.
So it's best to define it, so you'll have control,
just how the object membership test will unroll.

And if for optional methods you'll have started to thirst,
another one available is `__reversed__`.
It returns an iterator for doing backwards iteration,
but you'll only define it, if you beat the default computation,
that Python uses combining `__getitem__` and `__len__`
indexing backwards to 0, and then...

You'll find that you're done,
you've mastered container emulation
But your next set of magics form quite the combination

See, you briefly dipped your toe into the "index" operator
however you'll find the list of ops to support is oh so much greater
You'll think about `+` and `-` and start figuring
that the list of operators is biggering and biggering

The first giant list, you'll very soon encumber
it's the list of operators supported on a number

---

Let's start with just one that you can define,
`__add__` lets you support the plus sign
when your object is on the left with whatevers on the right
you return the added value, except when you might
reject the operation, because you don't know what to do,
and instead return the `NotImplemented` singleton value
such is the case if you dont recognize the type
of whatever the thing is on the right.

Then...

`__sub__` for subtraction, `__mul__` for times,
`__truediv`- of `floordiv` depending on the kind,
of division you want, true or integer, respectively
using one slash or two, for division, collectively.
And speaking of operations that come in pairs,
modulo arithmetic is a double-dunder-affair,
with `__mod__` for modulo support and then,
`__divmod__` to support the `divmod` builtin.
The last of the pairs of magic method gifts,
is `__l`- and `__rshift`
Then next up is `__pow__` for "to-the-power-of" support
whose operator is two askerisks, side-by-side, for short
and then, although the list was already so long
three more dunder methods will came along
`__and` - `xor`- and `or__`, oh come now, don't gripe,
they're how you support ampersand, caret and pipe.
And then, when your object supports the at-symbol,
the method you'll want is named `__matmul__`

AND THEN, that was it, there won't be more later
FOURTEEN methods for numeric operators,

unless...

Unless you think that there isn't enough.
[[ Here let's take a poll, is there other number stuff
we need to define? If yes raise your hand ]]
I see. I suppose our list should expand.

You'll maybe be asking yourself "O' teacher, how come?"
You'll ask yourself where these new methods are from
and how come my methods sometimes return `NotImplemented`,
if, to my caller, a `TypeError` is presented?

And so our list of methods then expands,
to support the same things with swapped operands,
but only if the result is `NotImplemented`
AND if two different types are presented,
Python tries again but this time with an "R",
at the front of the name, (it's not _that_ bizarre)
and calls this other method on the thing on the right,
let's see an example to bring how this works to light

Let's say someone subtracts from a `tuple` your `Foo`,
well `tuple` doesn't know what the heck to do,
so it's `__sub__`, then returns `NotImplemented`,
then the runtime continues on as documented,
noticing that `tuple` and `Foo` are different classes
and calls `Foo`'s `__rsub__`, and it passes
the tuple object on which we've acted
so `Foo` can say how it should be subtracted.

Now remember, you'll have to be dextrous and deft,
and try not to mix up a right "op" with a left,
when in an "r-method" you're the one on the right
getting this correct will make you seem bright

[[ How about another poll? That last one was fun.
Who thinks our numeric operator list is done? ]]

Me neither. As it turns out, and you'll see soon enough see
all but one of these operators' support requires THREE.
THREE dunders, at most, for each of these things
what _joy_ to us, supporting operators brings

"So what sets _these_ apart?" You'll groan and you'll grunt.
These last set of twelve has an "i" in the front.
They're meant to support doing the math "in-place",
mutating the object given in the left space,
for instance, `+=` uses `__iadd__`,
(completing the addition support triad).
However these methods you can actually omit,
they're there to help avoid copies a bit,
if one of these methods your type is lacking,
then `x = x + y` will be the fallbacking

If you kept watch, you might think I left one for later,
but no, `divmod` has no in-place operator.

---

Now, oh baby oh, how the operator list will still grow!
Regardless of lengthy class definitions you know.
You'll complain, and you'll curse, and you might even swear,
but you'll still need to learn the dunders to _compare_

The names of these methods really aren't at all surprising,
the brevity of each name is what's really quite appetizing,
using only 2 letters to represent each operator
for operations equality, lesser, and greater.

And exactly like the methods that I just reported
they return NotImplemented if the comparison isn't supported,
however this time there's no crazy switch-a-roo,
in this case a `TypeError` is raised unto you
And in the case the comparison is ok
a True or False as a return is the way.
Or anything truthy or falsey is ok,
it's turned into a boolean the Pythonic way.

Oh wait, forgive me, that's actually a new dunder
magics on magics, isn't Python a wonder.
Want to make your object seem `Falsey` or `True`?
You'll have to define `__bool__` too.

---

Last ones on our list (and yes it is still growing,
brevity, at this point we are simply forgoing)
You'll only need four more, so no need to get wary,
to support the operators _unary_.

`__neg`- `pos`, `abs`, and `invert` you'll learn
for `-`, `+`, `abs(`, and `~` `x`, in turn

---

<<<<Do I have time for more?!?!?!?!>>>>

---

To know most of them, including the ones this talk doesn't entail,
read docs.python.org/3/reference/datamodel.html
or just ask Google for the URL

Now, since your mountain is waiting, and as you go on your way,
remember the things I rememembered to you today,
and write all your code, the good, Pythonic way.

The End.

-->
