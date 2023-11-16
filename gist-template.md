# Find or Validate an Email Address with Regular Expression

Regular expressions (regex) can be a powerful tool for finding or validating email addresses in text. Here's a general regular expression that can be used to match a valid email address:

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

## TLDR

To begin, we're going to break down this *email address* regex point by point. However, please review the table of contents for more information on how regex works, so you can build your own.

1. `/` <br />
At the beginning and the end encapsulates the regex
2. `^`  <br />
Symbol to start, indicates that the match must start at the very beginning of the input string. This ensures that the entire email address is captured, not just a portion of it.
3. `([a-z0-9_\.-]+)`  <br />
This capture group matches the local part of the email address. This part appears before the `@` symbol. It is stating that this portion can be lower-case letters, numbers, underscores, hyphens, and periods. The `+` quantifier indicates that there must be at least one characer in this part.
4. `@`  <br />
The literal `@` symbol is used to separate the local part from the domain part of the email address. It's how we can tell an email address, is an email address.
5.  `([\da-z\.-]+)`  <br />
This capture group matches the domain part of the email address. This is the part of the email address that appears after the `@` symbol. It can be lower-case letters, numbers, hyphens, and periods. The `+` quantifier indivates that there must be at least one character in the domain part.
6.  `\.([a-z\.]{2,6})`  <br />
This capture group matched the top-level domain (TLD) of the email address. This is the part of the email address that appears after the last dot in the domain part (example: `.com`). It must consist of at least two characters and no more than six characters. It can contain lower-case letters and periods.
7. `$`  <br />
The dollar sign symbol at the end of the regex indicates that the match must end at the very end of the input string. This ensures that only complete email addresses are matched and prevents partial matches.


<!-- - how to define a search pattern in a body of text
- each character is a literal character (capital R, or lower-case a)
- meta character, meaning a character that does not indicate a single literal character. More so a generalized pattern.
- .* is a wildcard regular expression
- \d is a digit -->

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors

### Quantifiers

### Grouping Constructs

### Bracket Expressions

### Character Classes

### The OR Operator

### Flags

### Character Escapes

## Author
### Janet Webster
Full Stack MERN Software Engineer in training.

- [GitHub](https://github.com/TwixmixyJanet/)
- [LinkedIn](https://www.linkedin.com/in/twixmixy/)
- [Twitter](https://twitter.com/Twixmixy)
- [WakaTime](https://wakatime.com/@Twixmixy)

![Janet with her dog Winona on the beach](https://avatars.githubusercontent.com/u/117195025?v=4)

<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

Did you really read down this far? Gold star for you! ⭐
```
You have received 5+ points in being EXTRA
```
