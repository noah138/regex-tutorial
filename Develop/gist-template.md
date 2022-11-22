# Matching a URL using Regular Expressions

A regular expression, or regex, is a sequence of characters that allows you to create patterns to search for in text. This tutorial explains how to search for a url using a regex.

## Summary

The regex used to search for a url in is as follows:
`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`
Each character is in a specific order and combined with other characters to search exclusively for valid urls. In the following tutorial, I will explain the significance of each character and its placement in the regex.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)

## Regex Components

### Anchors

The characters `^` and `$` are considered anchors. The `^` anchor indicates the first character of the regex pattern, while `$` indicates the last character of the string. In all, we are looking for something that matches the pattern in between the anchor characters.

In our regex, we are looking for something that matches the pattern `(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?`.

### Quantifiers

Quantifiers signify the number of occurences of a character in the pattern we are looking for. Quantifiers affect the character(s) to their left.

The following characters are quantifiers:
- `*` - matches the pattern zero or more times
- `+` - matches the pattern one or more times
- `?` - matches the pattern zero or one times
- `{n}` - matches the pattern `n` number of times
- `{n,}` - matches the pattern at least `n` number of times
- `{n,x}` - matches the pattern from `n` to `x` number of times

There are several instances of quantifiers in our url regex:
- `https?` indicates that `s` matches the pattern zero or one times. This means that `http` - without the `s` - is accepted, as well as `https`. When looking to match a url, this solves the issue where urls can begin with either `http` or `https`.
- The following `?` in `(https?:\/\/)?` indicates that the inclusion of `http://` or `https://` is optional.
- `[\da-z\.-]+ ` means that a single digit(`d`), a group of letters (`a-z`), a dot (`.`), or a hypen (`-`) matches the pattern one or more times. This is refering the host name, which could include any of the latter characters.
- `[a-z\.]{2,6}` indicates that the a-z string and dot grouping that precedes it (`a-z\.`) must have at least two characters and no more than six. In this instance, this is referring to the sequence of characters after the dot in the domain name. For example, `https://google.com` would be matched, but `https://google.c` would not.
- `[\/\w \.-]*` indicates that the expression could match `/`, `//`, `www`, `.`, or `-`.
- The `/?` at the end of the expression indicates that the forward slash at the end of the url can be optional.

### Character Classes

A character class defines a set of characters, any one of which can occur in a string to fulfill a match.

Some common examples of character classes include;
- `\d` - matches a digit from 0-9
- `\w` - matches a word
- `\s` - matches a single space
- `.` - matches any character expect the newline character (`\n`)

### Grouping and Capturing



### Bracket Expressions



### Greedy and Lazy Match


## Author

Noah Schwartz - Github: [github.com/noah138](github.com/noah138)
