
# String Things

What's a String? Is that complicated? It sounds like something from advanced physics...

Well, not really. Strings are just text. Letters, numbers, spaces, special characters. Words and phrases, or a secret code, or total gibberish. English, or maybe some other language.

"But wait," you're thinking. "I thought programming was all about math!"

Well, not really. In the daily grind of most programmers, you do very little math, and not much with numbers. Strings play a much more fundamental role in most software developers' work.

Even if math is your forté, and you're planning to write hardcore math or science programs, or dive deep into hardware, I still think you should start with Strings. Strings are the interface between our programs and the people who use them. Any time you want to take input from a user, or output information to the user, it will be in the form of a String. And I want to make it *extremely* clear that nothing you do in programming will be remotely useful unless someone, a real living person, can use it.

Math may or may not be useful, depending on your domain. But you will always need the humble String. Make sure it's a friend, and a good one at that.

## Your First Program

Congratulations! You've made it to the traditional first exercise, the point in the book where I show you how to write a program that outputs the String, `"Hello World!"`  In some languages, this is a big deal. In Ruby, it's pretty straightforward.

First, you'll want to make sure you have access to a running Ruby environment.  You can follow the instructions in Appendix A (_Installing Ruby_), or Google to find an up-to-date tutorial. Once Ruby is installed, open up your command line (Terminal in Mac OS X, DOS Prompt in Windows), type `irb`, and press `Enter`. If you want to take a shortcut for now (but just for now!), head over to [repl.it](http://repl.it), where you can try out lots of different programming languages right from your browser. For now, just choose Ruby.

Here is your first program. Make sure to type it exactly, character by character.

```ruby
puts "Hello World!"
```

Your output should look something like this:

```ruby
2.3.0 :001 > puts "Hello World!"
Hello World!
 => nil 
```

Whoa, there's a lot going on there! Let's break it down.

First, we have the current version of Ruby (in my case, `2.3.0`, but don't worry if yours is different) and a line number (`001` because it's the first line of the program). Then there's a `>` which tells you that you can start typing!

Your program itself has 2 parts:

1. The command `puts`
2. The String `"Hello World!"`

`puts` is how you tell Ruby to output text to the command line. `"Hello World!"` is a String. In Ruby, Strings are bits of text surrounded by either double quotes (`"`) or single quotes (`'`). Make sure you're not writing your code in a fancy program like Microsoft Word, which will turn your quotes into "smart quotes" (`‘’` and `“”`). Ruby doesn't know what those are, so it won't treat them as things which mark off a String, and your program will probably fail to run!