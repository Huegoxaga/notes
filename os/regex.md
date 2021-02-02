# Regular Expression

## Introduction

- It is a sequence of characters that define a search pattern.
- It will be "executed" on a string and return a search result.
- Matches will be found if a given string has this pattern.
- The result can be represented by a boolean value or indices.
- It was created in the 1950s, then introduced in the UNIX world.
- The pattern is surrounded by a set of `/`.
- Go to [regexr.com](https://regexr.com) to test, practice and learn more about regular expression.

## Syntax

### Literal Matches

- The characters inside will be searched as a pattern one by one.
- `/a/` will search for the character `a`.
- `/abc/` will search for characters `a` immediately followed by `b`, then `c`.(or word `abc`).

### Metacharacters

- They are placed inside the pattern to add special rules.
- When the literal meanings of the following characters are needed, prepend a `\` to escape.
- `\`
  - Escape metacharacters
  - Whitespace characters
    - `[\b]` backspace
    - `\f` form feed
    - `\n` line feed
    - `\r` carriage return
    - `\t` tab
    - `\v` vertical tab
    - The use of the whitespace characters is highly dependent on the current OS.
  - Shorthand character classes
    - `\d` means `[0-9]`
    - `\D` means `[^0-9]`
    - `\w` means `[0-9a-zA-Z_]` It will match a character that is a alphanumeric character or underscore.
    - `\W` means `[^0-9a-zA-Z_]`
    - `\s` means `[\f\n\r\t\v]`
    - `\S` means `[^\f\n\r\t\v]`
    - `\b` add a word boundary `\bhello\b` will only match word hello surrounded by spaces.
    - `\B` add a word boundary `\Bhello\B` will match word hello not surrounded by spaces.
- `^` The caret
  - can be used to negated character sets.
    - `/[^0-9]/` it will match any character that is not number.
    - `/[^0-9^a-z^A-Z]/` it also works for multiple character sets.
    - `/[^abc]/` it will match any character that is not `a`, `b` or `c`.
  - can be used to find match only at the beginning of the string(anchor).
    - `/^A/` it will match the leading `A` in a given string.
    - In a pattern, nothing should be entered before the beginning anchor.
- `$` can be used to find match only at the end of the string(anchor).
  - `/A$/` it will match the trailing `A` in a given string.
  - In a pattern, nothing should be entered after the end anchor.
- `.` It matches any single character.
  - empty space will match.
  - line breaks won't match.
- `?`
  - Optional
    - It matches any one character or null at a given location.
      - `/a?c/` matches `ac`, `abc`, `adc`, etc.
    - The optional characters can be grouped as `()?`
      - `/Dec(ember)?/` matches both `December` and `Dec`
  - lazy matching
    - add the `?` after any quantifier, to make the quantifier return the shortest result possible, in case of overmatching.
- `*` A quantifier that matches zero or more character before it in the pattern.
  - `/[0-9]*A/` returns any group of numbers followed by `A` and return all the character `A`.
- `+` A quantifier that matches one or more character before it in the pattern.
  - `/[0-9]+/` returns any group of numbers.
- `()` grouping, a pattern surrounded by `()` can be used by another pattern as sub-pattern.
  - In extended `Regex`, `(o{2})\1` is the same as `o{2}o{2}`
- `[]` It creates character classes(character sets).
  - The occurrence of any one of the characters list inside `[]` will result a match for one character in a given string.
    - `/[Gg]r[ea]y/` will match `Grey`, `Gray`, `grey`, `gray`.
  - `-` can be used to set a range.
    - `/[A-Z]/` will match any capital letters.
    - `/[A-Za-z]/` will match any letters.
    - The order of the character on the left side and right side of `-` matters.
    - Metacharacters inside the `[]` do not need to escaped for literal meanings.
      - Except for `^` at the beginning.
- `|` A vertical bar separates alternatives.
  - `/gray|grey/` can match `gray` or `grey`.
- `{}` a quantifier for interval matching.
  - `/[a-z]{3}/` matches a group of 3 letter which is between `a` and `z`.
  - `/[a-z]{3,6}/` matches a group of 3 to 6 letter which is between `a` and `z`.
  - `/[a-z]{3,}/` matches a group of 3 to infinite letter which is between `a` and `z`.

### Flags

- A flag can be appended to the end of the pattern.

#### In Javascript

- `/g` return an array of all matches, not just the first match.
- `/i` case insensitive.
- `/m` multiline
- `/y` sticky
- `/u` unicode
- `/s` single line(dotall)

#### In Python

- `re.A` or `re.ASCII` - Make \w, \W, \b, \B, \d, \D, \s and \S perform ASCII-only matching instead of full Unicode matching.
- `re.DEBUG` - Display debug information about compiled expression. No corresponding inline flag.
- `re.I` or `re.IGNORECASE` - Perform case-insensitive matching
- `re.L` or `re.LOCALE` - Make \w, \W, \b, \B and case-insensitive matching dependent on the current locale.
- `re.M` or `re.MULTILINE` - When specified, the pattern character '^' matches at the beginning of the string and at the beginning of each line; and the pattern character '\$' matches at the end of the string and at the end of each line.
- `re.S` or `re.DOTALL` - Make the '.' special character match any character at all, including a newline;
- `re.X` or `re.VERBOSE` - Whitespace and comments within the pattern is ignored.
