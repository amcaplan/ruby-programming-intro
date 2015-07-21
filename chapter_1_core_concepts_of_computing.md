## The Core Concept of Computing
You've probably heard a lot of things about computer programming.  Here are a few things someone may have warned you about:
1. Programming is difficult
2. Programming requires complex thought patterns
3. You need to keep a ton of information in your head
4. You need to memorize a lot of details
5. Computer programs have scary syntax
6. You need to know tons of math

Most of these are neither 100% true nor 100% false.  What is certainly true is this: You don't need to worry about everything right away.

In this chapter, we will introduce one simple concept which lies at the core of all things programming.  This is an idea we will return to again and again, so it's important to understand clearly before we move on.

The idea is this:

> Computers understand 2 things:
1. Data
2. Instructions.

Computers are pretty dumb machines at the heart of it all.  Way down deep, they have information stored as sets of 1s and 0s (often better thought of as on/off), and they can be told to flip those back and forth.  That's it.

So how do computers do wildly complex things like banking, launching rockets, guiding airplanes, calculating statistics, or 3D animation?  It turns out that you can represent information quite effectively with those little 1s and 0s, and computers can manipulate that information incredibly quickly.

#### A Small Detour: Turing Completeness
Once upon a time, there was a pretty smart guy named Alan Turing, today considered one of the forefathers of modern computing.  Turing invented a hypothetical machine, which he called an "a-machine."  This device would be fed an infinite stream of tape marked with squares containing symbols.

The machine could do two things.  First, it could manipulate the symbols according to a set of rules.  Second, it could move the tape back and forth.

Put simply, Turing argued that anything which can be calculated by other methods could be figured out using this machine.

From time to time, you may hear that a language or system is "Turing complete."  This just means that it can calculate anything that a Turing machine can.  In other words, a "Turing complete" language can be used to write a program to figure out anything that can be figured out by a computer.

You may have already figured out where this is going.  A Turing machine has 2 parts:
1. The tape that goes through it
2. The machine using rules to modify the tape

We can translate this back to our point above:
1. Data
2. Instructions

That's all a computer needs to accomplish anything you'll ever want it to do.

## Modeling
Without getting too technical just yet, let's try a simplistic explanation of how 