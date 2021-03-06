# 😕Regular Expressions😁

Regular Expressions are notoriously difficult to learn - they have a very compact syntax that ends up looking like gibberish. However, they can be extremely powerful when it comes to form validation, find and replace tasks, and/or searching through a body of text. The following cheatsheet provides common RegEx examples and techniques for the JavaScript developer.

🔥 There are several awesome tools that can help you debug RegEx in the browser - my personal favorite is [RegExr](https://regexr.com/) .

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

## Flags

Expression flags change how the expression is interpreted. Flags follow the closing forward slash of the expression (ex. `/.+/igm` ).

- `i` Ignore case makes the whole expression case-insensitive. For example, `/aBc/i` would match `AbC`
- `g` To search or extract a pattern more than once

# How to Use RegEx in JavaScript

## Create a Regular Expression

There are two ways to create a regular expression in JavaScript. The literal way is just a set of characters between two forward slashes `/ /`.

```js
const re = /foo/;
```

You can also instantiate `RegExp`.

```js
const re = new RegExp(/foo/);
```

# String Regex Functions

There are several ways to use a regular expression on a string primitive, such as (1) `match` all the occurrences, (2) `search` for the existence of a pattern, or (3) `replace` matches with a new value.

```js
let myString = "Hello, World!";
let myRegex = /Hello/;
let result = myRegex.test(myString);
// Output: true

const matches = "aBC".match(/[A-Z]/g);
// Output: Array [B, C]

const index = "aBC".search(/[A-Z]/);
// Output: 1

const next = "aBC".replace(/a/, "A");
// Output: ABC
```

# Common Examples

## Phone numbers validation

If you want to use regular expression for validating phone or mobile numbers followed by country code. For example if you want to validating Italian mobile numbers followed by +39, then you can use the following regex:

```js
const re = /(\+39[\-\s])\(?([0-9]{3})\)?[-. ]?([0-9]{3})[-. ]?([0-9]{4})$/;
```

Or a simplified version for any country code:

```js
const re = /^(\+\d{2}[\-\s]?)\d{10}$/;
```

## Password Validation

How do you validate the format of a password for a signup form? Let’s force passwords to contain a capital letter, lowercase letter, number, and min length of 8.

```js
const re = /^(?=.*\d)(?=.*[a-z])(?=.*[A-Z])(?=.*[a-zA-Z]).{8,}$/g;

"1sMyPasswordOK?".search(re);
```

## Hex Codes

How do you find all of the hex codes, such as CSS colors, in a document? Useful if you need to analyze the color scheme.

```js
const re = /#?([\da-fA-F]{2})([\da-fA-F]{2})([\da-fA-F]{2})/g;

"color: #ffffff; color: #000000;".match(re);
```

## Remove HTML Tags

How do you remove all HTML tags from a document? Use the regex below to find and replace all HTML tags.

```js
const re =
  /(<script(\s|\S)*?<\/script>)|(<style(\s|\S)*?<\/style>)|(<!--(\s|\S)*?-->)|(<\/?(\s|\S)*?>)/g;

const sanitized = "<h1>Hello World</h1>".replace(re, "");
```
