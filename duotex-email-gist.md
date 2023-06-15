# Duotex

In this tutorial we will be examinging how to construct an email matching regular experession.  These are commonly used in sign up forms for the entry of an email address for submission to a query. In a nutshell the regular expression, or regex for short, elaborates what characters an expected standard email address is constructed with.  This functions to limit the intake of the querey to a specified structure, thus making database management ruely. The purpose of this tutorial is to deconstruct and explain the regex of any standard email address.

## Summary

For a typical email address, there will be a specific pattern that may seem familiar, example structure somename@someorganization.some
While it may be possible to construct an aborhation of the above, the pattern is highly recognizable to an email address.  Althought the example is fictious for this tutorial, it may even lead to an existing inbox!  Below is the regex (regular expression) notation for any possible standard email address. By the time you reach the end of this tutorial, you will understand the expression. 

Matching an Email – /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)

## Regex Components

A standard email has the format:

 /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

First we will name the parts that make up this expression, and in the following sections below the parts will be further broken down into cited explanations.  While we limit this regex example to an email address, the concepts are applicable to describing the syntax of any regular expression in various coding languages in general.


* literal: " / " (forward slash).
* anchors: " ^ " and " $ " (carrot and cash).
* bracket expressions: " [here] " (square bracket), what's here is what counts.
* grouping: " (here) " (parentheses), aka subexpression.
* operators: " @ " (at and plus symbols).
* characters: " A-Z0-9_\._- " (various key characters).
* boundaries: " /^ and $/ " (literal and anchor).

[a-z0-9_\.-]
[\da-z\.-]
[a-z\.]{2,6}

(+)@(+).(){}
/^ and $/ 



### Anchors


>https://coding-boot-camp.github.io/full-stack/computer-science/regex-tutorial
>
>A regex is considered a literal, so the pattern must be wrapped in slash characters (/).
>
>The characters ^ and $ are both considered to be anchors.
>
>The ^ anchor signifies a string that begins with the characters that follow it.
>
>The $ anchor signifies a string that ends with the characters that precede it.
>  
>Anything inside a set of square brackets ([]) represents a range of characters that we want to match. These patterns are known as bracket expressions, but they are also known as a positive character group, because they outline the characters we want to include.


### Quantifiers

From the Request-Responce full stack blog, we get the following explanation of Quantifiers:

>Quantifiers set the limits of the string that your regex matches (or an individual section of the string). They frequently include the minimum and maximum number of characters that your regex is looking for.
>
>Quantifiers are inherently greedy, meaning they match as many occurrences of particular patterns as possible. They include the following:
>
>*—Matches the pattern zero or more times
>
>+—Matches the pattern one or more times
>
>?—Matches the pattern zero or one time
>
>{}—Curly brackets can provide three different ways to set limits for a match:
>
>{ n }—Matches the pattern exactly n number of times
>
>{ n, }—Matches the pattern at least n number of times
>
>{ n, x }—Matches the pattern from a minimum of n number of times to a maximum of x number of times
>
>Each of these quantifiers can be made lazy by adding the ? symbol after it, meaning it will match as few occurrences as possible.
>
>https://coding-boot-camp.github.io/full-stack/computer-science/regex-tutorial


### OR Operator

In our case, we are using the AND boolean operator, while the use may be simular, the meaning is different. Basicaly, an email address is constructed with a username AND organization.

(+)@(+).(){}


### Character Classes

The following explanation of characters is from the regex tutorial:
https://eloquentjavascript.net/09_regexp.html

A number of common character groups have their own built-in shortcuts. Digits are one of them: \d means the same thing as [0-9].

\d	Any digit character
\w	An alphanumeric character (“word character”)
\s	Any whitespace character (space, tab, newline, and similar)
\D	A character that is not a digit
\W	A nonalphanumeric character
\S	A nonwhitespace character
.	Any character except for newline

### Flags

ToDo with the @ symbol, specifically an email expression will always contain this character.  If an expression without @ is entered in the textbox, the query is rejected, since all emails will have the symbol.  Simularly, the [a-z\.]{2,6} says the address must end with a suffix from 2 to 6 characters long, preceeded by a period.

### Grouping and Capturing

The following explanation of matching is from the regex tutorial:
https://eloquentjavascript.net/09_regexp.html

Matches and groups
The test method is the absolute simplest way to match a regular expression. It tells you only whether it matched and nothing else. Regular expressions also have an exec (execute) method that will return null if no match was found and return an object with information about the match otherwise.

let match = /\d+/.exec("one two 100");
console.log(match);
// → ["100"]
console.log(match.index);
// → 8
An object returned from exec has an index property that tells us where in the string the successful match begins. Other than that, the object looks like (and in fact is) an array of strings, whose first element is the string that was matched. In the previous example, this is the sequence of digits that we were looking for.

String values have a match method that behaves similarly.

console.log("one two 100".match(/\d+/));
// → ["100"]
When the regular expression contains subexpressions grouped with parentheses, the text that matched those groups will also show up in the array. The whole match is always the first element. The next element is the part matched by the first group (the one whose opening parenthesis comes first in the expression), then the second group, and so on.

let quotedText = /'([^']*)'/;
console.log(quotedText.exec("she said 'hello'"));
// → ["'hello'", "hello"]
When a group does not end up being matched at all (for example, when followed by a question mark), its position in the output array will hold undefined. Similarly, when a group is matched multiple times, only the last match ends up in the array.

console.log(/bad(ly)?/.exec("bad"));
// → ["bad", undefined]
console.log(/(\d)+/.exec("123"));
// → ["123", "3"]

```bash
https://eloquentjavascript.net/09_regexp.html
```


### Bracket Expressions


[a-z0-9_\.-]
[\da-z\.-]
[a-z\.]{2,6}

### Greedy and Lazy Match

Script for identifying an email. We will use this in identifying and aggregating data, beyond the scope of storing to a database list.


### Boundaries

We begin and end our regex expression with boundaries.
/^ and $/ 
Notice this is constructed of the literal and anchor pattern, bounding what is inbetween.

>https://eloquentjavascript.net/09_regexp.html
>If we want to enforce that the match must span the whole string, we can add the markers ^ and $. The caret matches the start of the input string, whereas the dollar sign matches the end.

## Author

Thank You for taking the time to read this gist about the regex of an email expression.  In case you were wondering, this was created by me, Gary, an actuall human.  I am producing this explanation to reach out to other humans to explain the syntax of machine language and culture one bit at a time.  You may learn more about me and by work by following the link to my github profile.  When you are there, be sure to check out my Portfolio to get a good sample and link to contact.

https://github.com/gdutra2002 