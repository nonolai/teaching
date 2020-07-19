# Lesson 3 - The Atom

When I was little, my dad loved to explain the world to me. It's probably a big
part of why I devoured science later in my life. I loved these lessons, despite
occasionally being long winded, but the rest of my family groaned every time one
started. Because my dad always started from the beginning:

Explanation on nuclear energy?

"Well, this is the atom...<sup>[1](#fn-thetalk)</sup>"

Explanation on why the sky is blue?

"Well, this is the atom..."

Explanation on supply and demand in economics?

"Well, this is the atom..."

That's what this lesson is. This is the atom.

## Giving Directions

### Simple Directions

Imagine, for a second, that you're driving to your friend's
house<sup>[2](#fn-driving)</sup>. You don't know how to get there, and you
ask your friend for directions. Now usually, they'd just give you a link to
directions on your phone, but your friend is a die-hard computer scientist.
Instead, they give you a file that contains only the words "left" and "right".
She tells you that at every turn, just read the next word and do it. It takes
you approximate 5 days longer than it needed to, but eventually you make it to
your friend's place.

Ignoring the parts about electronics,
[Wikipedia's definition of a computer](https://en.wikipedia.org/wiki/Computer)
is "a machine that can be instructed to carry out sequences of arithmetic or
logical operations automatically..." Your friend just turned you into a
rudimentary computer with a single instruction (turn). You took a list of
instructions and carried out those operations automatically.

### How Binary Gets Into It

Say the next time you visit your friend, you forgot the
directions<sup>[3](#fn-shame)</sup>. She's a good friend, though, so she heard
your complaint that the many pages of directions were far too much. So instead,
she gives you a page and a half of 0s and 1s. 0 means turn left, and 1 means
turn right. You make it to your friend's house, it takes at least as long, but
this time at least you didn't kill as many trees to get the directions printed.

Your friend has just binary encoded your instructions. It's not terribly
intuitive for humans, but CPUs<sup>[4](#fn-cpu)</sup> are far better at working
with numbers than the patterns that humans are built to quickly decipher. You
begin to suspect your friend has been spending too much time on her CS homework.

### More Instructions

You resolve to drag your friend outside and save her from this CS nonsense. You
grit your teeth and decide to reuse the last instructions she gave you, but
your friend, not knowing your intentions, claims that you need to use her new
instructions! She's optimized the algorithm, you'll get there in a fraction of
the time!

She sends you another page of 0s and 1s, but this time, 0 means to go straight
through the intersection and 1 means that you will need to turn. If the number
following the 1 is a 0, turn left, otherwise turn right. In pseudocode:

```text
for each index i in the input
  if input[i] == 0
    drive through the intersection
  else if input[i] == 1:
    if input[i + 1] == 0:
      turn left
    else:
      turn right
    skip the next iteration of the loop (so we don't interpret the direction as
    an instruction)
```

Now you have two instructions! Your friend has turned you into a computer with
two instructions. But you successfully make it to her house and drag her
outside to remind her what sunlight looks like. Hopefully this saves your
friendship.

## Tying it In

### Machine Language/Binary

The language you and your friend established in the the above example is a
`machine language` containing various instructions you know know how to
execute. Included is a notion of being able to pass additional data to those
instructions. This is similar to the bit<sup>[5](#fn-bit)</sup> patterns that
CPUs understand.

### Assembly

Your friend could start replacing the first bit of each instruction with a
small word that explains what it does. Replacing 0 (go straight) with `cont`
and 1 with `turn`, we would get instructions that look a bit like:

```text
cont
cont
turn 0
turn 1
cont
turn 0
```

Which is a very simple `assembly` language. We can compile it down to
`machine language`: 1's and 0's that a CPU would understand.

### And Higher

All _compiled_ programming languages build on this hierarchy. They give you a
set of keywords and ways to specify values that they can compile to a language
closer to what the machine understands.

Examples of compiled languages are ones such as C++, Rust, and Go.

### An Aside on Interpreted Languages

Interpreted programming languages are written by programmers similarly to
compiled languages. However, instead of the commands they write being compiled
all the way down to binary for the CPU, they are executed by a program that can
interpret the keywords as they come in.

Examples of these are Javascript and Python.

There are also languages that are compiled down to an intermediary language for
their `interpreter` program. They live on the spectrum somewhere between "pure"
compiled or interpreted languages.

An example of this sort of language would be Java.

## Exercises

This has mostly been theory so far, but as an exercise (in any language of your
choice), implement an interpreter. It should be able to:

1.  Read a file containing 1s and 0s as defined in your
    friend's<sup>[7](#fn-whytho)</sup> last directions.
2.  Print out "Start", "Continue Straight", "Turn Left", "Turn Right", and "You
    Have Arrived".

--------------------------------------------------------------------------------

<a name="fn-driving"><sup>1</sup></a> Thankfully, he didn't start this way when
giving me "the talk".

<a name="fn-driving"><sup>2</sup></a> God I miss the world before pandemic.

<a name="fn-shame"><sup>3</sup></a> Shame on you.

<a name="fn-cpu"><sup>4</sup></a> CPU = Central Processing Unit

<a name="fn-bit"><sup>5</sup></a> A bit is a single 1 or 0.

<a name="fn-whytho"><sup>6</sup></a> Why are you still friends with this person?