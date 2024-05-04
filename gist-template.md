# Title (replace with your title)

In this tutorial I will explain the regex used to validate email addresses :
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

## Summary

This regex is used to validate email addresses. It does this by assuring the input string follows the the template for an email address (user@doman.extension). The regex allows the username to contain digits, lowercase letters, dots, and hyphens. The extension can contain lowercase letters and dots, but can only be between 2 and 6 characters long. The domain can contain digits, lowercase letters, dots, and hyphens.

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

^ and $ are anchors. They establish the start and finish of a line. The email credentials must start at the beginning and end at the end of the anchors.

Anchors are used to establish the specific position to a line of text, they do not count in that line of text the way non-anchor characters do.

$ is used as the end of an anchor. When it's placed at the end of an expression, it establishes that the pattern that follows must be at the end of the line. For example, abc$ will match any line ending in abc.

^ is used as the start of line anchor. It is used at the beginning of an expression, and establishes the pattern after must start at the beginning of the line. ^abc will match any line that starts with abc.

when used together as in ^abc$, they will match an entire line only comprised of abc, any additional characters would establish a no match.

let regex = /^abc$/;
console.log(regex.test("abc")); // true
console.log(regex.test("abcd")); // false
console.log(regex.test("abcdabc")); // false
console.log(regex.test("abcabc")); // false

### Quantifiers

'+' is a quantifier that means one or more of the preceding element. The {2,6} establishes between 2 and 6 of the preceding element.

Quantifiers used in regualr expressions establish how many instances of the preceding element are required for a match.

'+' means one or more

{a,b} means between "a and b"

### Grouping Constructs

The () are used for grouping and capturing. They group the regex into the username, domain, and extension.

Grouping and capturing allow you to group together parts of your pattern, which can then be treated as a single unit. This is done using parentheses ().

Grouping

Grouping is useful when you want to apply a quantifier to multiple characters. For example, in the regex (ab)+, the + quantifier applies to the entire group ab, not just the character b. This regex will match "ab", "abab", "ababab", etc.

In the context of the email matching regex, grouping is used to separate the email address into three parts: the username, domain, and extension. This is done by surrounding each part with parentheses, like so: ([a-z0-9_\.-]+), ([\da-z\.-]+), and ([a-z\.]{2,6}).

Capturing

In addition to grouping, parentheses also create a capturing group. A capturing group "captures" the part of the string matched by the part of the regex inside the parentheses. These captured groups can then be referred back to with backreferences (using \1, \2, etc.).

In the email matching regex, there are three capturing groups corresponding to the username, domain, and extension of the email address. However, this regex does not use backreferences, so the capturing feature is not utilized in this case.

It's important to note that not all parentheses create capturing groups. If you want to group without capturing, you can use non-capturing parentheses, which are written as (?:...).

### Bracket Expressions

this regex uses bracket expressions to determine a range of characters that can be used in the email address.

You can use [] in regular expression to match any one character out of a set of characters.

Inside [] you can establish a range of characters, or specific characters. [a-z] will match to the entire a-z lower character case, while [a] will only match to a.

In the context of the email matching regex, bracket expressions are used to specify the range of characters that can be used in different parts of the email address:

([a-z0-9_\.-]+): The bracket expression [a-z0-9_\.-] specifies that the username part of the email address can contain any one lowercase letter (a-z), digit (0-9), underscore (\_), dot (.), or hyphen (-).
([\da-z\.-]+): The bracket expression [\da-z\.-] specifies that the domain part of the email address can contain any one digit (\d is a shorthand character class that matches any digit), lowercase letter (a-z), dot (.), or hyphen (-).
([a-z\.]{2,6}): The bracket expression [a-z\.] specifies that the extension part of the email address can contain any one lowercase letter (a-z) or dot (.).

### Character Classes

The email regex uses the character classes [a-z0-9_\.-], [\da-z\.-], and [a-z\.].

Username: [a-z0-9_\.-]: This character class matches any one lowercase letter (a-z), digit (0-9), underscore (\_), dot (.), or hyphen (-).

Domain: [\da-z\.-]: This character class matches any one digit (\d is a shorthand character class that matches any digit), lowercase letter (a-z), dot (.), or hyphen (-).

Extension: [a-z\.]: This character class matches any one lowercase letter (a-z) or dot (.).

## Author

Written by Jeremy Sevilla

Github: https://github.com/jrsevi
