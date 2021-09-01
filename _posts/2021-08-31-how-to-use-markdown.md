---
layout: post
title: "How to use markdown"
date: 2021-08-31 16:04:50 +0200
categories: cheatsheet
tags: web, blog, markdown
---

Let's learn basic `Markdown` syntax

- Index
  - [What is Markdown?](#what-is-markdown)
  - [Why Markdown?](#why-markdown)
  - [Which editor should I use?](#which-editor-should-i-use)
  - [Basic Markdown Syntax](#basic-markdown-syntax)

## What is Markdown?

> `Markdown` is a [lightweight markup language](https://en.wikipedia.org/wiki/Lightweight_markup_language) for creating [formatted text](https://en.wikipedia.org/wiki/Formatted_text) using a [plain-text editor](https://en.wikipedia.org/wiki/Text_editor).

## Why Markdown?

- **For web writing**

  You can perfectly convert your text in HTML. It's light weight and that make it easy to storage.

- **For every software**

  Since this is a plain text format, it is usable and openable in any devices, and OS. It has only one filetype (unlike MSWord or any other word processors), so software doesn't need to keep up with the format.

- **Simple but powerful enough**

  Easy to add text modifiers like lists, bold, italics, etc. And you can insert tables too.

- **For productive writing**

  Markdown is easy and simple to learn and use than HTML or any other web programming language. For exemple, with Markdown language, you don't need to close every tags like you do with HTML.

- **For version management**

  Since it is plain text, it's easy to manage versions through `Git` .

## Which editor should I use?

- [**Prose.io**](https://prose.io/)
  - A web-based interface.
  - You can create, edit, delete files, and save the changes **directly** to `GitHub`
  - It has advanced support for [`Jekyll`](http://jekyllrb.com/) sites
- [**StackEdit**](https://stackedit.io/)
  - You can sync in `GoogleDrive`, `Git`, `Tumblr`
  - You can collaborate with your colleagues at the same time.
  - support for mathematical expressions, diagrams, scores, Emojis.
- [**MarkdownPad**](http://www.markdownpad.com/)
  - You can download from the link (free version and pro version)
  - You can use it off-line
  - for Windows

* **[MacDown(for MAC)](https://macdown.uranusjr.com/)**
  - Opensource
  - Highly customisable Markdown rendering
* [**Typora(for Mac)**](https://typora.io)
  - Minimal design
  - Seamless live preview

# Basic Markdown Syntax

> Type the lines in the codeblocs one by one with your editor to learn. You'll see the simplicity and usefulness of Markdown.

- **[Step1] `Headings`**

  To create a heading, add number signs (`#`) in front of a word or phrase. The number of number signs you use should correspond to the heading level.

```markdown
# Heading level 1

## Heading level 2

### Heading level 3

#### Heading level 4

##### Heading level 5

###### Heading level 6
```

**Renderd output:**

# Heading level 1

## Heading level 2

### Heading level 3

#### Heading level 4

##### Heading level 5

###### Heading level 6

---

- **[Step 2] `Horizontal Rules`**

```mark
---
***
___
```

**Renderd output:**

---

---

---

---

- **[Step 3] `Line Break`**

```mark
put <br>to break line
```

**Renderd output:**

put <br>to break lines

---

- **[Step 4]** **`List` **

```mark
Ordered List
1. First
1. Second
1. Third

Undordered List
+ Unordered
  - A
    * B
      + C
```

**Renderd output:**

Ordered List

1. First
1. Second
1. Third

Undordered List

- Unordered
  - A
    - B
      - C

---

- **[Step 5] `Emphasis`**

```markdown
**Bold**
_Italic_
~~strikethrough~~
<u>underline</u>
**BOLD*italic*BOLD AGAIN**
```

**Renderd output:**

**Bold**
_Italic_
~~strikethrough~~
<u>underline</u>
**BOLD*italic*BOLD AGAIN**

---

- **[Step 6] `Blockquote`**

```markdown
> Dorothy followed her through many of the beautiful rooms in her castle.
>
> > The Witch bade her clean the pots and kettles
> >
> > > and sweep the floor and keep the fire fed with wood.
```

**Renderd output:**

> Dorothy followed her through many of the beautiful rooms in her castle.
>
> > The Witch bade her clean the pots and kettles
> >
> > > and sweep the floor and keep the fire fed with wood.

---

- **[Step 7] `Link`**

``` 
Type1(To create a link in `Link text`) : [Google](https://google.com "tooltip when you hover over")
Type2(To create a link exposing the URL) : <https://theorydb.github.io>
Type3(a link to a paragraprh in the article) : [Markdown Syntax 1 (Basic)](#markdown-syntax-1-basic)
```

---

- **[Step 8] `Image)`**

```markdown
Type1(insert an `image`) :
![Image](https://oulico.github.io/assets/img/2021-08-31-how-to-use-markdown/cat.jpeg "cat")

Type2(If you want to`change the size`, use HTML tag) :
<img src="https://oulico.github.io/assets/img/2021-08-31-how-to-use-markdown/cat.jpeg" width="300" height="200">

Type3 (to make a `link in image` ) :
[![Image](https://oulico.github.io/assets/img/2021-08-31-how-to-use-markdown/cat.jpeg "cat")](https://en.wikipedia.org/wiki/Cat)
```

Type1(insert an `image`) :
![Image](https://oulico.github.io/assets/img/2021-08-31-how-to-use-markdown/cat.jpeg "cat")

Type2(If you want to`change the size`, use HTML tag) :
<img src="https://oulico.github.io/assets/img/2021-08-31-how-to-use-markdown/cat.jpeg" "cat" width="300" height="200">

Type3 (to make a `link in image` ) :
[![Image](https://oulico.github.io/assets/img/2021-08-31-how-to-use-markdown/cat.jpeg "cat")](https://en.wikipedia.org/wiki/Cat)
