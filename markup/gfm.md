# GFM

- GFM is Github Flavored Markdown.
- It is Github's own version of markdown syntax. All `.md` file in Github follows its Syntax.
- It is consisted of standard markdown syntax and additional features supported by GFM.
  `.md` or `.markdown` extension.

## Syntax

### Inline HTML

Raw HTML can be used in the Markdown file, and it'll mostly work pretty well.

### Headers

#### Example:

```md
# This is an h1 tag plus a horizontal line after. alternatively use = below each character

## This is an h2 tag plus a horizontal line after. alternatively use - below each character

### This is an h3 tag

.
.
.

###### This is an h6 tag
```

#### Result:

# This is an h1 tag plus a horizontal line after. alternatively use = below each character

## This is an h2 tag plus a horizontal line after. alternatively use - below each character

### This is an h3 tag

.
.
.

###### This is an h6 tag

### Emphasis

#### Example:

```md
_This text will be italic_
_This will also be italic_
**This text will be bold**
**This will also be bold**
_You **can** combine them_
```

#### Result:<br>

_This text will be italic_<br>
_This will also be italic_<br>
**This text will be bold**<br>
**This will also be bold**<br>
_You **can** combine them_

### Lists

#### Unordered

```md
- Item 1
- Item 2
  - Item 2a
  - Item 2b

* also works
```

- subpoints follow two spaces.

#### Ordered

```md
1. Item 1
2. Item 2
3. Item 3

- Item 3a
- Item 3b
```

### Images

```md
![Alt Text](url)
![image name](/images/logo.png)
```

### Links

```md
[Text](url)
[GitHub](http://github.com)
http://github.com - automatic!
```

- Using `#header-name` as link for content in the page.
- `#header-name-1` for the second header with the same name in the page.

### Block Quotes

```
> Hello World!
```

#### Result:<br>

> Hello World!

### Backslash escapes

```md
\*literal asterisks\*
```

### Horizontal Lines

```
Use one of the following
Three or more...
---  Hyphens
***  Asterisks
___  Underscores
```

### Strikethrough

Any word wrapped with two tildes, like `~~this~~`, will appear crossed out.

### Metions

`@username` explicitly mention the user to view the comment.

### Code blocks

- Inline Code blocks
  wrapped in a set of \`\`.

```
``int x = 12;``
```

- Fenced Code blocks
  using a set of \`\`\` at the first line and the last line of the code block
- Fenced Code blocks with syntax highlighting
- use a language identifier after \`\`\` in the first line, language identifier including: \*

### Issue References

- Any number that refers to an Issue or Pull Request will be automatically converted into a link.

```
 #1
github-flavored-markdown#1
defunkt/github-flavored-markdown#1
```

### Emoji

GitHub supports emoji:

```
:+1: :sparkles: :camel: :tada: :rocket: :metal: :octocat:
```

#### Result:

:+1: :sparkles: :camel: :tada: :rocket: :metal: :octocat:

### Task Lists

```
- [x] task1
- [ ] task2
- [x] task3
- [x] task4
```

#### Result: <br>

- [x] task1
- [ ] task2
- [x] task3
- [x] task4

### Tables

create tables by assembling a list of words and dividing them with hyphens - (for the first row), and then separating each column with a pipe |

```
First Header | Second Header
------------ | -------------
Content cell 1 | Content cell 2
Content column 1 | Content column 2
```

#### Result: <br>

| First Header     | Second Header    |
| ---------------- | ---------------- |
| Content cell 1   | Content cell 2   |
| Content column 1 | Content column 2 |

### YouTube Videos

They can't be added directly but you can add an image with a link to the video like this:

```
<a href="http://www.youtube.com/watch?feature=player_embedded&v=YOUTUBE_VIDEO_ID_HERE " target="_blank"><img src="http://img.youtube.com/vi/YOUTUBE_VIDEO_ID_HERE/0.jpg"  alt="IMAGE ALT TEXT HERE" width="240" height="180" border="10" /></a>
```

### Comments(to be tested)

Text can be hidden in <!- -Text- -> or <Text>
[//]: # (This syntax works like a comment, and won't appear in any output.)

# Gitbook

- a CLI tool that auto convert `.md` file into webpages.

## Setup

- Installation `npm i gitbook-cli -g`
- Create Project, in project folder`gitbook init`
- in project file `SUMMARY.md` is the menu
- Preview, `gitbook serve`
- At the end of the line, the URL can be used to view the content.

## Build Website

- Run `gitbook init` everytime when change it made.
- if `SUMMARY.md` is updated, init will add new files in the project folder.
- `{{` or `}}` in `.md` files in code block will cause error, place a space in between to avoid errors. Ex, `{ {`
- all code must be in code block.
- Run `gitbook build`
- Use `gitbook build ./ --log=debug --debug` to debug.

## Publish

- github pages host static webpages from repo, it is free.
- add the generated webpages files in the GitHub Repo
- in Settings, find GitHub Pages Section and Set the folder location for hosting.
- The Theme if for `.md` pages.

## Escape Special Symbols

Use a keyword `raw` and `endraw` surrounded by `{`(outter) and `%`(inner) to escape special symbols that causes build error
