# Find or Validate an Email Address with Regular Expression

Regular expressions (regex) can be a powerful tool for finding or validating email addresses in text. Here's a general regular expression that can be used to match a valid email address:

```
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```

## TLDR

To begin, we're going to break down this **email address** regex point by point. However, please review the table of contents for more information on how regex works, so you can build your own.

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

In this tutorial I will be showing you how regex can be utilized. For this tutorial we will be using the email address example and each aspect of how regex it used will be discussed through that point of view.

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
Regex anchors are special characters that don't match any characters themselves, but instead assert something about the position of the match within the string. They are used to restrict the range of possible matches for a regular expression pattern. Let's break these down.

#### Types of Regex Anchors

1. `^` (Caret): Matches the beginning of a string
2. `$` (Dollar Sign): Matches the end of the string
3. `\A`: Matches the beginning of the string, considering newline characters as part of the string
4. `\z`: Matches the end of the string, excluding newline characters
5. `\b` (Word Boundary): Matches the position between a word character and a non-word character or vice versa
6. `\B` (Non-Word Boundary): Matches the position within a word or before/after a punctuation mark or whitespace

#### Examples of Anchor Usage

1. `^dog`: Matches the word "dog" only if it appears at the beginning of the string
2. `cat$`: Matches the word "cat" only if it appears at the end of the string
3. `^\d+$`: Matches a string that consists only of digits (numbers)
4. `\Bdog\B`: Matches the word "dog" if it appears within another word or before/after a punctuation mark or whitespace, like "It was a dogpile"

#### Impact of the `m` Flag (Multiline Mode)

By default, the `^` and `$` anchors match only the beginning and end of the entire string. However, when the `m` flag is set, these anchors also match the beginning and end of each line within the string.

#### Applications of Regex Anchors

1. __Validating Input:__ Anchors can be used to ensure that user input adheres to specific formats, like emails
2. __Extracting Specific Data:__ Anchors can be used to extract specific portions of text from a larger string, such as URLs or file names
3. __Searching for Specific Patterns:__ Anchors can be used to find patterns that occur at specific positions within a text, such as words at the beginning of lines or numbers at the end of lines

### Quantifiers

Regex quantifiers are metacharacters that specify how many times the preceding character or group should be matched in regular expressions. They are used to indicate the number of occurrences of a character or group, making it easier to match patterns of varying lengths.

#### Types of Quantifiers

There are five main types.
1. __Zero or more (*):__ Matches the preceding character or group zero or more times <br />
_For example: The regex pattern `colou*r` will match "colour", "colouur", "colouuuuuur", etc._
2. __One or more (+):__ Matches the preceding character or group one or more times <br />
_For example: The regex pattern `colou+r`will match "colour", "colouur", "colouuuuuur", (etc), but not "color"._
3. __Zero or one (?):__ Matches the preceding character or group zero or one time <br />
_For example: The regex pattern `colou?r` will match "color" and "colour"._
4. __Exactly n times ({n}):__ Matches the preceding character or group exactly n times
_For example: The regex pattern `colou{3}r` will match "colouuur", but not "colour" or "colouuuur"._
5. __Between n and m times ({n},{m}):__ Matches the preceding character or group between n and m times
_For example: The regex pattern `colou{2,3}r` will match "colouur" and "colouuurr", but not "colour" or "colouuuurrr"._

#### Greedy versus Lazy Quantifiers

Some quantifiers have two versions: greedy and lazy. Greedy quantifiers try to match as many times as possible, while lazy quantifiers try to match as few times as possible. You can turn a greedy quantifier into a lazy quantifier by adding a "?".
For example: the regex pattern `colou+?r` will match "color" and "colour", while the regex pattern `colou*+r` will match "colour", "colouur", "colouuuur", and so on.

Quantifiers are a powerful tool for matching pattersn in strings. They are used in many different applications, including text processing, data validation, and web scraping.

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
