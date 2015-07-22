# The Core Concept of Computing

You've probably heard a lot of things about computer programming.  Here are a few things someone may have warned you about:
1. Programming is difficult
2. Programming requires complex thought patterns
3. You need to keep a ton of information in your head
4. You need to memorize a lot of details
5. Computer programs have scary syntax
6. You need to know tons of math

Most of these are neither 100% true nor 100% false.  What is certainly true is this: You don't need to worry about everything right away.

In this chapter, we will introduce one simple concept which lies at the core of all things programming.  This is an idea we will return to again and again, so it's important to understand clearly before we move on.

The idea is this.

> Computers understand 2 things:
1. Data
2. Instructions.

Computers are pretty dumb machines at the heart of it all.  Way down deep, they have information stored as sets of 1s and 0s (often better thought of as on/off), and they can be told to flip those back and forth.  That's it.

So how do computers do wildly complex things like banking, launching rockets, guiding airplanes, calculating statistics, or 3D animation?  It turns out that you can represent information quite effectively with those little 1s and 0s, and computers can manipulate that information incredibly quickly.

#### A Small Detour: Turing Completeness
Once upon a time, in the early 20th century, there was a pretty smart guy named Alan Turing, today considered one of the forefathers of modern computing.  Turing invented a hypothetical machine, which he called an "a-machine."  This device would be fed an infinite stream of tape marked with squares containing symbols.

The machine could do two things.  First, it could manipulate the symbols according to a set of rules.  Second, it could move the tape back and forth.

Put simply, Turing argued that anything which can be calculated by other methods (such as humans with pencils and paper) could be figured out using this machine.

From time to time, you may hear that a language or system is "Turing complete."  This just means that it can calculate anything that a Turing machine can.  In other words, a "Turing complete" language can be used to write a program to figure out anything that can be figured out by a computer.

You may have already figured out where this is going.  A Turing machine has 2 parts:
1. The tape that goes through it
2. The machine using rules to modify the tape

We can translate this back to our point above:
1. Data
2. Instructions

That's all a computer needs to accomplish anything you'll ever want it to do.

## Modeling
Without getting into code just yet, let's try a bare-bones explanation of how computers figure things out.

#### Example 1: Do the Math

Let's start with a math problem.

WARNING: It will be a bit messy.  Just remember, the general concept is most important here, so don't get bogged down in the details.

If I feed a computer the expression
```
2 + 3
```
it has to somehow figure out that this equals 5.  To make that happen, the computer needs some kind of internal representation of 2, 3, and 5.

Since computers speak in 1s and 0s, their number system is binary, also known as base 2.  By contrast, our usual system is base 10, meaning that the tenth number is represented as "10."  We count 9 numbers - 1, 2, 3, 4, 5, 6, 7, 8, 9 - and then for the tenth, we jump to 2 digits.  Computers have no way of representing 2 or more with 1 digit, so instead, the first ten numbers are: 1, 10, 11, 100, 101, 110, 111, 1000, 1001, 1010.  We jump to a new number of digits at every exponent of 2: 2 (2<sup>1</sup>), 4 (2<sup>2</sup>), 8 (2<sup>3</sup>), 16 (2<sup>4</sup>), etc.

Once computers can map numbers we understand (2 and 3) to numbers they can understand (10 and 11, respectively) they can add the two.  To do so, we will need an **algorithm** - a set of instructions for how to carry out that operation.  Let's suggest an algorithm.

Starting from the right, consider each pair of numbers.  Then apply the following rules (don't worry if they're a bit confusing, you won't need to remember the details):

1. If it's 0 and 0, the number in our result will be 0.
2. If it's 1 and 0, or 0 and 1, the number in our result will be 1.
3. If it's 1 and 1, the number in our result will be 0, and the next column gets an extra 1 to consider.

Since we will have cases where the 1 is carried, let's write the rules for those scenarios too:

<ol start="4">
  <li>If it's 1, 0, and 0, the number in our result will be 0.</li>
  <li>If it's 1, 0, and 1, or 1, 1, and 0, the number in our result will be 0, and the next column gets an extra 1 to consider.</li>
  <li>If it's 1, 1, and 1, the number in our result will be 1, and the next column gets an extra 1 to consider.</li>
</ol>

One more rule to round it out:

<ol start="7">
  <li>If at the end we have a 1 left over, it gets added to the front of the result.</li>
</ol>

Whew, that was a mouthful!  But the good news is, we've just implemented addition as a simple set of if-this-then-that rules which don't actually involve any math.  Cool!

Let's quickly apply them to our problem.  Rewritten in the format we suggested, this looks like:
```
 10
+11
---
???
```
Resolving column 1 with Rule 2:
```
 10
+11
---
??1
```
Resolving column 2 with Rule 3:
```
1
 10
+11
---
?01
```
Then we tack on our 1 from Rule 7:
```
 10
+11
---
101
```
Presto, 101!  Er, 5, that is.

This was a relatively simple (if confusing!) example.  All in all, we just figured out how to add 2 numbers. But we have already learned a few things:
* Ideas that humans relate to can be mapped to things computers can understand.  Those make up our _data_.
* We need to define **algorithms** through which computers interpret that information.  These are our _instructions_.

I don't know about you, but I don't learn best through math.  I need something real-world.  So let's have a more relatable example!

#### Example 2: Don't Have a Cow!

Congratulations, you've just founded Silicon Valley's hottest new startup, Cows 4 Cash.  You're in the business of helping farmers turn their surplus bovines into cold, hard cash.  As such, you need a program to keep track of the farmers selling their cows, the buyers, and the money changing hands.

Somewhere in your program, you will need to store a representation of the farmers, the cows, the buyers, and the money.  You will also need to work out the steps of each transaction, something like:
  1. A farmer posts a cow for sale
  2. A buyer selects a cow to buy
  3. The buyer pays using a credit card
  4. The farmer gets a Certified Eco-Friendly<sup>®</sup> cow-shipping container delivered in the mail
  5. The farmer ships the cow
  6. The buyer confirms receipt of the cow

Your program needs to have detailed instructions about what needs to be done at each step of the way.  For example, a farmer can decide to un-post a cow as long at is has not yet been bought, but the farmer cannot refuse to ship the cow once a payment is made.  You need to teach the computer that steps 1 and 2 aren't permanent, but steps 3 and on are irrevocable.

The information about the state of your various parties - humans, cows, money - that's your _data_.  The business rules for how the transactions are conducted - that's your _instructions_.

The cool part about all this: Your computer doesn't really need to *understand* anything about humans, cows, or money.  It just needs to know that there is something called a farmer, another thing called a buyer, a thing called a cow... you get the picture.  It also needs to know how they relate to each other.  It can keep track of cow sales without deeply understanding cows or sales.

This is the wonderful, dirty little secret about programming.  We never actually teach our computers to understand anything.  All we need is for our computers to act like they understand things.  It turns out that this play-acting is useful enough to do all the amazing things computers can do today.

#### Putting It All Together

We in the programming community have a word for this play-acting: *Modeling*.  We take a real-world problem and create a model system in our program which mimics the actual things that are happening.

Sometimes, our goal is to push the model forward and see what happens.  Perhaps we are writing a chemistry program that models molecules, and we want to see what happens under certain conditions.

Often, though, the relationship runs in the opposite direction; we want our programs to influence the world.  We model people, or things, in our program, and when our program receives indication that something should happen to those people or things, they actually happen.

When I order an item online, I've just caused a program to register a purchase.  But that purchase causes people in a warehouse to ship me the item I ordered.

When I set my thermostat to different temperatures at different times throughout the day, I'm just inputting data.  But it uses that data to determine how it should heat or cool my house.

Modeling is the bridge between computer-speak and the human understanding of the world.  It's a powerful and critical concept.  You will spend a lot of time thinking about the "right" way to model your system when designing your programs.

## Wrapping Up
Let's quickly sum up what we've learned in this chapter.
* Computers are only capable of taking in ***data*** and executing ***instructions*** related to (and possibly modifying) that data.
* We don't need to teach computers anything.  We just feed them data and tell them what to do with it.
* ***Algorithms*** are the expression of a coherent task as a set of simple instructions.
* Through ***modeling***, we bridge the gap between what computers understand and what humans need them to do.

We've covered a lot of ground already!  In the next chapter, we'll move on from this theoretical stuff and start actually writing some code.