# GFM

- GFM is Github Flavored Markdown.
- It is Github's own version of markdown syntax. All `.md` file in Github follows its Syntax.
- It is consisted of standard markdown syntax and additional features supported by GFM.
  `.md` or `.markdown` extension.

## Syntax

### Inline HTML

- Raw HTML can be used in the Markdown file, and it'll mostly work pretty well.
- Styling can be added to the HTML tag:
  - align content, `<div align="center"></div>`
  - styling images, `<img align="left" width="200" height="100" />`

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

```md
`int x = 12;`
```

- Fenced Code blocks
  using a set of \`\`\` at the first line and the last line of the code block
- Fenced Code blocks with syntax highlighting
- use a language identifier after \`\`\` in the first line, language identifier including: \*
- use the following ways to print `` ` `` inside code block

  ```md
  use backslash to escape when backtick is printed outside code blocks
  Print a singe \` inside code blocks `` ` ``
  Use higher number of \` to print more \` inside code blocks ` `` ` (print two)
  `` text`  `` produces text\`
  `` `text `` produces \`text
  `` `text` `` produces \`text\`
  ```

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

```md
| First Header     | Second Header    |
| ---------------- | ---------------- |
| Content cell 1   | Content cell 2   |
| Content column 1 | Content column 2 |
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

### LaTeX

- Insert LaTeX code in an `img` tag as `https://render.githubusercontent.com/render/math?math=x = -1`
  - `+` need to be replaced by its percent-encoding value which is `%2B`.
- Another to way insert`![$x=1+a$](https://render.githubusercontent.com/render/math?math=%24x%3D1%2Ba%24)`
  - It works only when there is no space in the path. Can replce space with its encoded value `%20`.
  - [Click](https://alexanderrodin.com/github-latex-markdown/) to use the LaTeX image link generator tools for GFM.
    - This generator does not encode `(` which is `%28` and `)` which is `%29`. It should be changed manually.
- If hosted by `GitBook.com`, `LaTeX` syntax will be recognized if formula is surrounded by `$$`

# GitBook

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

#### Escape Special Symbols

Use a keyword `raw` and `endraw` surrounded by `{`(outter) and `%`(inner) as html comments to escape special symbols that cause build errors

## Publish

- github pages host static webpages from repo, it is free.
- add the generated webpages files in the GitHub Repo
- in Settings, find GitHub Pages Section and Set the folder location for hosting.
- The Theme if for `.md` pages.

## Export as PDF

- Install [Calibre](https://calibre-ebook.com/download)
- run `PATH=$PATH:/Applications/calibre.app/Contents/MacOS/`
- run `gitbook pdf`
