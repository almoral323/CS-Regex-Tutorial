# How to Use Regular Expressions AKA Regex

A regular expression, colloquially referred to as a "regex" (REGular EXpressions) is a group of characters used to search through a string of text. Common uses for regular expressions include: advanced find and replace, validation, rearranging, and numerous other powerful methods. 

## Summary

In this limited look at regular expressions, we'll be taking a look at how they can be applied to perform e-mail pattern matches. The regular expression for e-mail patterns is: 
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`<br>
We'll be taking an in-depth look at the anatomy, components, and practical uses for this regex.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Bracket Expressions](#bracket-expressions)
- [Grouping Constructs](#grouping-constructs)
- [Full Analysis](#full-analysis)
- [Author](#author)

## Regex Components
So how does a regular expression differ from any other string of characters? Regular expressions can be spotted first with the intuitive syntax of beginning and ending the expression with a forward slash "`/`" (e.g. `/`bulldog`/`, `/`dishsoap`/`, et cetera).<br>
As you can see from our regex example in the Summary, there are MANY other characters at play within the confines of our opening and closing forward slashes- we'll take a closer look at what they are and how they work in this section. (It should be noted that characters can be placed OUTSIDE of the regex to give us unique searching and filtering powers, however for the intended scope of this gist we'll be focusing on what goes inside of the regex.)<br> Lets dissect our e-mail search regex<br>`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`<br>and make some sense of it all, piece by piece. 

### Anchors
The contents of our regex begin with a `^` and end with a `$`. These two characters, called "anchors", indicate where to start and stop the search expression. For example, let's say we want to find the phrase "red" in an enormous database of addresses. How do we return only "`red`" and not addresses that include "tailo`red`" or "`red`dit"? This is where our anchors come in: the `^` keeps out all information that precedes our search, and the `$` shaves off extra characters from the end of our search.

### Bracket Expressions
Next, you'll note that portions of our regex are encapsulated in brackets `[ ]` and parentheses `( )`. Brackets will specify a set of characters to match and return any character referenced here. In our example we see this three times:<br>
`[a-z0-9_\.-]` `[\da-z\.-]` and `[a-z\.]`<br>
A hyphen can be used to create a class or set of characters, as we see in the first bracket expression `a-z`, meaning any letter from a to z will be returned. Adding a hyphen as the first or last character in the set will represent it as a literal hyphen to be included in the overall search, as is seen in the first two examples.
Parentheses, as in arithmetic, are used to group regular expression. This is useful in applying *quantifiers* to sections of the regex, which we'll visit next.

### Quantifiers
With regular expressions, quantifiers tell us how many times a portion of our expression will be repeated. We have two such components in our regex: the `+` and `{2,6}`. The former, `+`, means that we can have any amount of characters, provided that the number is more than 1. For our `{2,6}` we're specifying a match of 2-6 times, giving us 2-6 characters at most.

### Grouping Constructs
Another great feature of regular expressions is not simply matching and returning information, but also extracting information for further processing. In our mail search example, we see multiple such groupings (covered in Bracket Expressions). Grouping our search allows us to add or ignore portions of the expected results returned, effectively searching within a search. Let's say we wanted to match and return every address from a database of government addresses (...mail.mil, ...mail.gov, etc.), but we didn't care which agency or department their address ended with. By performing our original search, then grouping our parameters to EXCLUDE the address suffix, we can ensure that we're only pulling government addresses, while still omitting their department from the matched results.

## Full Analysis
Now that we've got a tacit understanding of the anatomy of our regex<br>
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`<br>
Let's break down what it means overall:
Our regex is grouped into `group`+`@`+`group`+`.`+`group`, giving us a vague outline of the "xxxx@xxxx.xxxx" format that we've all seen time and time again. The format is constrained by our anchors, the content is constrained by the alphanumeric values we've specified, and the quantifiers we've laid out are applied to those groups. 

## Author
Alfredo Morales


Github- almoral323
