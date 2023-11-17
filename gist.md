# Find or Validate an Email Address with Regular Expression

Regular expressions (regex) can be a powerful tool for finding or validating email addresses in text. Here's a general regex that can be used to match a valid email address:

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
This capture group matches the local part of the email address. This part appears before the `@` symbol. It is stating that this portion can be lowercase letters, numbers, underscores, hyphens, and periods. The `+` quantifier indicates that there must be at least one characer in this part.
4. `@`  <br />
The literal `@` symbol is used to separate the local part from the domain part of the email address. It's how we can tell an email address, is an email address.
5.  `([\da-z\.-]+)`  <br />
This capture group matches the domain part of the email address. This is the part of the email address that appears after the `@` symbol. It can be lowercase letters, numbers, hyphens, and periods. The `+` quantifier indivates that there must be at least one character in the domain part.
6.  `\.([a-z\.]{2,6})`  <br />
This capture group matched the top-level domain (TLD) of the email address. This is the part of the email address that appears after the last dot in the domain part (example: `.com`). It must consist of at least two characters and no more than six characters. It can contain lowercase letters and periods.
7. `$`  <br />
The dollar sign symbol at the end of the regex indicates that the match must end at the very end of the input string. This ensures that only complete email addresses are matched and prevents partial matches.

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
Regex anchors are special characters that don't match any characters themselves, but instead assert something about the position of the match within the string. They are used to restrict the range of possible matches for a regex pattern. Let's break these down.

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

Regex quantifiers are metacharacters that specify how many times the preceding character or group should be matched in regex. They are used to indicate the number of occurrences of a character or group, making it easier to match patterns of varying lengths.

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

Grouping constructs are fundamental elements of regex that allow you to group subexpressions, apply quantifiers to multiple patterns, and capture matched substrings. They play a crucial role in constructing complex and sophisticated regex.

#### Purpose of Grouping Constructs

1. __Grouping Subexpressions:__ They enable you to group multiple regex patterns into a single unit, allowing you to apply quantifiers, assertions, or other expressions to the entire group.
2. __Quantifying Multiple Patterns:__ Grouping constructs enable you to apply quantifiers to multiple patterns simultaneously. For instance, the pattern `(ab){2}` matches two consecutive occurrences of the substring "ab".
3. __Capturing Matched Substrings:__ Grouping constructs can be used to capture matched substrings for further processing or replacement. Captured groups can be accessed using backreferences.

#### Common Grouping Constructs

1. __Parentheses ():__ Parentheses are the most common grouping construct in regex. They group subexpressions and allow quantifiers to be applied to the entire group.
2. __Non-capturing Groups (?P>):__ The non-capturing group construct, denoted by `(?P<>)`, groups subexpressions without capturing the matched substrings. This is useful when you want to group patterns for quantifiers or assertions but don't need to capture the matched text.
3. __Named Groups `(?P<name>)`:__ Named groups allow you to assign unique names to subexpressions, making them easier to reference in backreferences or replacement operations.
4. __Lookahead and Lookbehind Assertions:__ Named groups allow you to assign unique names to subexpressions, making them easier to reference in backreferences or replacement operations.

Grouping constructs are essential tools for building powerful and versatile regex. They enable you to group patterns, apply quantifiers precisely, capture matched substrings, and refine matching conditions using assertions.

### Bracket Expressions

Bracket expressions, also known as character classes, are a fundamental component of regex that allow you to specify a set of characters to match. They are enclosed in square brackets (`[]`) and can be used to match a single character or a range of characters.

#### Matching Single Characters

To match a single character, simply list the character within the square brackets. For instance `[a]` matches the lowercase letter "a," while `[Z]` matches the uppercase letter "Z."

#### Matching Character Ranges

To match a range of characters, use a hyphen (-) to indicate the start and end of the range. For example, `[a-z]` matches any lowercase letter from "a" to "z," and `[0-9]` matches any decimal digit from 0 to 9.

#### Negating Character Classes

To negate a character class, place a caret (`^`) at the beginning of the square brackets. This matches any character except those listed within the brackets. For instance, `[^a-z]` matches any character except lowercase letters, and `[^0-9]` matches any character except decimal digits.

#### Matching Multiple Character Classes

You can combine multiple character classes into a single pattern using the pipe (`|`) symbol. This matches any character that belongs to any of the specified classes. For example, `[a-z0-9]` matches any lowercase letter or decimal digit.

#### Escaping Characters

Certain characters, such as `.` (period), `^` (caret), `$` (dollar sign), `*` (asterisk), `+` (plus sign), `?` (question mark), `\` (backslash), and `()`, have special meanings in regex. To match these characters literally, you need to escape them by placing a backslash (`\`) before them. For example, `\.` matches a literal period, `\^` matches a literal caret, and `\\` matches a literal backlash.

### Character Classes

Character classes, also known as character sets, are a fundamental component of regex used to match specific characters or groups of characters within a string. They are defined using square brackets (`[]`) and allow you to specify a range of characters or negate a set of characters.

#### Matching a Single Character from a Set

To match any single character from a specified set, enclose the characters within square brackets. For instance, the character class `[abc]` matches any of the characters 'a', 'b', or 'c'.

#### Matching a Range of Characters

To match a range of characters, use a hyphen (-) between the characters. For example, `[a-z]` matches any lowercase letter from 'a' to 'z'. Similarly, `[0-9]` matches any digit from 0 to 9.

#### Negating a Character Class

To match any character except for those specified in the character class, place a caret (`^`) at the beginning of the character class. For instance, `[^abc]` matches any character that is not 'a', 'b', or 'c'.

#### Matching Specific Character Classes
Certain predefined character classes represent common sets of characters.

- `\d`: Matches any digit from 0 to 9.
- `\D`: Matches any character that is not a digit.
- `\s`: Matches any whitespace character, including spaces, tabs, newlines.
- `\S`: Matches any character that is not a whitespace character.
- `\w`: Matches any word character, including letters, digits, and underscores (_).
- `\W`: Matches any character that is not a word character.

### The OR Operator

The OR operator, represented by the pipe symbol (|), is a fundamental operator in regex that allows for matching multiple alternative patterns. It essentially provides a choice between two or more patterns, indicating that any of the specified patterns will satisfy the matching criteria.

1. __Multiple Patterns:__ The OR operator can connect two or more regex patterns, allowing you to match any of the specified patterns.
2. __Alternative Matching:__ The OR operator indicates that any of the connected patterns is a valid match for the regex.
3. __Order of Application:__ The OR operator is applied left to right, meaning it evaluates the patterns sequentially until a match is found.
4. __Matching Efficiency:__ If a match is found with the first pattern, the second and subsequent patterns are not evaluated.
5. __Grouping with Parentheses:__ You can use parentheses to group patterns and apply the OR operator within the group.
6. __Nested OR Operators:__ You can nest OR operators within each other to create more complex matching criteria.

### Flags

Regex flags or regex options, are optional modifiers that can be used to alter the behavior of regex. The are typically denoted by single lowercase letters placed at the end of a regex pattern. These flags provide various functionalities, such as performing case-insensitive searches, matching multiple occurrences of a pattern, or enabling support for Unicode characters.

1. `i` (ignore case): This flag makes the regex case-insensitive, meaning it matches both uppercase and lowercase characters interchangeably. For instance, the pattern "/a/i" matches all occurrences of the letter "a" or "A" in a given string.
2. `g` (global): This flag tells the regex to find all occurrences of the pattern in the string, rather than just the first one. Without the "g" flag, the regex stops searching after finding the first match.
3. `m` (multiline): This flag enables multiline mode, which affects the behavior of the caret (`^`) and dollar sign (`$`) anchors. In multiline mode, `^` matches the beginning of any line, and `$` matches the end of any line.
4. `u` (Unicode): This flag enables support for Unicode characters, allowing the regex to match characters beyond the Basic Multilingual Plane (BMP).
5. `s` (single-line): This flag treats the entire string as a single line, causing the dot (`.`) metacharacter to match newlines as well as any other character.
6. `y` (sticky): This flag restricts the search to the last match position. It only finds matches from the position where the previous match ended.

These flags can be combined to achieve specific search behaviors. For example, "/color.*/gi" searches for all occurrences of the word "color" following by any number of characters, regardless of case, across multiple lines in the string.

Regex flags play a crucial role in enhancing the flexibility and power of regex, enabling them to handlemore complex and nuanced search tasks.

### Character Escapes

Regex character escapes are used to inform the regex engine that a specific character should be interpreted literally rather than as a metacharacter. Metacharacters have special meanings within the regex and are used to define patterns or constructs. By escaping a character, you tell the engine to treat it as an ordinary character rather than its special meaning.

The backslash (`\`) symbol is used to escape characters in regex. When you precede a character with a backslash, it instructs the negine to interpret that character as itself. 

__Here are some common regex character escapes:__

| Character |	Escaped Form |	Meaning |
| ----- | ----- | ----- |
| .	| .	| Matches any single character except for a newline |
| + | + | Matches one or more of the preceding character |
| *	| *	| Matches zero or more of the preceding character |
| ? |	? |	Matches zero or one of the preceding character |
| ^ |	^ |	Matches the beginning of a string |
| $ |	$ |	Matches the end of a string |
| ( |	( |	Starts a capturing group |
| ) |	) |	Ends a capturing group |
| [ |	[ |	Starts a character class |
| ] |	] |	Ends a character class |
| { |	{ |	Starts a quantifier |
| } |	} |	Ends a quantifier |
| \ |	\ |	Escapes a backslash |

Escaping characters is essential when matching literal occurrences of metacharacters or when you want to use a character in a way that conflicts with its special meaning.

### In Summary

There is a LOT that goes into any regex. There's no way to remember all of this information and I would *highly* recommend using your favorite regex documentation to build what you are trying to accomplish. Questions? Hit up the old google.com or your preferred AI!

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
