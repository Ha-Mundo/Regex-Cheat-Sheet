# Regular Expressions

Regular Expressions are notoriously difficult to learn - they have a very compact syntax that ends up looking like gibberish. However, they can be extremely powerful when it comes to form validation, find and replace tasks, and/or searching through a body of text. The following cheatsheet provides common RegEx examples and techniques for the JavaScript developer.

🔥 There are several awesome tools that can help you debug RegEx in the browser - my personal favorite is RegExr (regex.com).

# Regex Reference

## Basics

- `/ expression / flags`, i.e `/[A-Z]+/g` basic format
- `/ hello\?\*\\/` escape special characters with backslashes
- `()` group with parentheses
- `|` logical OR

## Character classes

- `\w` word `\d` digit `\s` whitespace (tabs, line breaks)
- `\W` NOT word `\D` NOT digit `\S` NOT whitespace
- `\t` tabs, `\n` line breaks
- `.` any character (except newline)

## Brackets

- `[xyz]` match any x, y, z
- `[J-Z]` match any capital letters between J & Z.
- `[^xyz]` NOT x, y, z

## Quantification

- `bob|alice` match bob or alice
- `z?` zero or one occurrences
- `z*` zero or multiple occurrences
- `z+` one or multiple occurrences
- `z{n}` n occurrences
- `z{min,max}` min/max occurrences

## Anchors

- `hello world` exact match
- `^hello` start of the strings
- `world$` end of the string

# How to Use RegEx in JavaScript
