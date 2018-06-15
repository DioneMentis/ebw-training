---
title: Connecting humans and machines
---

# Connecting humans and machines
{:.no_toc}

* TOC here
{:toc}

When you're editing for multi-format publishing, you never want to have to edit the same content again for each new format. You want to work on **one, master document,** and you expect that machines will convert that document into any number of formats later on.

If you're creating content that a machine will process, we need to write in a way that both humans and machines can understand. This is not easy: humans are flexible and love breaking rules; machines are not flexible, and are made of rules.

Luckily, in building the Internet people have come up with all kinds of conventions and techniques for capturing human stories in ways that machines can handle.

As editors, we need to learn about those techniques so that machines will do what we want, and not break our work.

## Markup

Anyone who worked in publishing twenty years ago remembers marking up manuscripts for typesetting: adding feature tags like `[start box]` and `[end box]` and inserting instructions for design like `[blank page]` or `[italics]`.

> Today it's extremely rare for a book to be final at third pages. Later in this course we'll talk about how the publishing industry lost these skills when MS Word ruined everything, and how we might relearn them.
{:.sidenote}

In well-organised teams, we standardised those tags so that typesetting would be fast and hopefully error-free. With a standardised language for manuscript markup in a team, was not unusual for a book to be final at the third round of page proofs.

While we were doing that, around the world people were doing the same thing for web pages. Though rather than marking up content for typesetters, they were marking up content for web browsers: machines that would 'typeset' on the fly, on screen, on a user's computer.

There were many attempts to create markup languages. The technique that really caught involved wrapping text in angle-bracket tags (like `<box>`). Your team could create and extend its own markup language for any kind of content. This technique became known as 'extensible markup language', or XML for short. 

There are probably tens of thousands of markup languages created using the XML technique. The most popular by far is HTML, or hypertext markup language. ALmost every web page you visit is delivered to your computer in HTML, and your web browser reads the HTML and 'typesets' the page for you automatically.

If well constructed, that HTML markup lets browsers lay out the same content differently, but readably, on an infinite number of viewport shapes and sizes, including printable pages.

You don't need to be able to write HTML to be a multi-format editor. You only need to know, more or less, how it works.

### A five-minute guide to HTML

To tell a machine that a given string of characters is a paragraph, we use a `<p>` tag:

`<p>Hello World!</p>`

The `<p>` is a 'paragraph' tag. We use paragraph tags at the start and end of the paragraph, and the slash in the second tag indicates that it's closing the paragraph.

A paragraph marked up with `<p></p>` tags is an 'element'. The word 'element' is also useful in traditional book terms for any piece of a book, for what we often call a feature, like a figure or a blockquote.

#### Elements

HTML includes about a hundren standard elements. In publishing, these are the most important ones:

> As in everything, HTML gets more complicated than this. There are different kinds of HTML with slightly different tags. As en editor you will almost never have to worry about that.
{:.sidenote}

*   `<p>` for paragraph
*   `<ul>` for unordered list (i.e. a bulleted list, but it might not actually have visible bullets)
*   `<ol>` for ordered list (e.g. a 1, 2, 3 or a, b, c list)
*   `<li>` for list item, an item in an ordered or unordered list
*   `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`, `<h6>` for six levels of heading
*   `<img>` for image
*   `<a>` for a clickable link (the 'a' happens to stand for anchor)
*   `<em>` for emphasising words (as you might use italics in print)
*   `<strong>` for making words stand out (as you might use bold in print)
*   `<span>` for any string of letters you need to mark for any reason (as in, this span `<span>spans three words</span>`)
*   `<div>` for division, any block of text or images you need to mark for any reason
*   `<table>` for a table
*   `<tr>` for a table row
*   `<td>` for a table cell in a row (`td` stands for table data).

#### Classes

As you may have guessed, in most books there are several different kinds of paragraph. There are, for instance, lead-ins, taglines, epigraphs, dedications, and so on.

We can't have separate elements for all of those. So in HTML we say there are different *classes* of paragraph. You can just think up classes as you need them. The same goes for any of the elements I listed:

*   lists might be regular bulleted lists, clickable menus, chapter objectives, or glossary entries;
*   images might be portraits, graphs, icons, decorations, or maps;
*   spans might mark computer code, important words, proper names, places, or other special terms;
*   divs might mark sections as sidebars, footnotes, or activities.

And much more. We can't just use `<p>` for everything, because then every class of paragraph would look the same.

> If you're sharp, you'll have noticed that none of these elements or classes describe what the text or image they mark up *looks like*. They only describe its *function or purpose*. 
> 
> All appearance or formatting is managed separately, in another file called a stylesheet. We'll get to that later.
{:.sidenote}

So HTML lets us invent our own classes, and gives us a way to say what class an element belongs to. We do this by adding an *attribute* to the element's opening tag. Let's say we want to call our paragraph a 'greeting' paragraph:

`<p class="greeting">Hello World!</p>`

We could have called the class anything we liked, including something silly:

`<p class="frabjous-day">Hello World!</p>`

It's best to use class names that are easy to remember and that describe their purpose clearly. And it's good to reuse the same classes in your team and across your publications, for consistency.

## Character encoding and unicode

Character encoding is about the most technical thing we're going to cover. 

So let's keep it short:

1. **Computers are binary**. That is, they only think in on–off, yes–no, 1–0. Humans say 'ones and zeros' to describe this.
2. So, to a computer, a **letter or number is a pattern of ones and zeros,** e.g. `01000001` can represent the letter 'A', and `01000010` the letter 'B'.
3. There are many characters to encode in this way. Over the years, official bodies have established conventions for character sets. The most important character set is called **Unicode,** which is a list of about 100&nbsp;000 characters (and growing, especially with emojis).
4. The most common pattern for encoding these Unicode characters in ones and zeros is called **UTF-8**.
5. In theory, every computer file should state its character encoding inside it, so that your computer knows how to display its characters. (Programs like MS Word should automatically add that data inside your files.)
6. If you open a document, or a web page or ebook, and the characters look wrong, it's usually because the document and your computer are using different character sets.

What does that mean for editors?

When we're working in simple English, this means almost nothing. Just keep going and computers will do the rest.

But as soon as you start working with special characters, it's critical that you use unicode characters.

Let's say you want to insert a degrees symbol, '°'. That symbol is not on your keyboard, and you're not sure ho to insert it. Authors will often insert an o (the lowercase letter 'oh'), and make it superscript using formatting tools. That is a Very Bad Idea!

Let's say you send the file to someone else, who copies and pastes your `30°C` into a different software program. Their program handles superscript differently, or doesn't support it at all. Now they have an o where you intended a degree symbol: `30oC`!

This is just one common example. As you work, you'll find many cases where authors misuse incorrect characters, rather than the correct unicode character.

**So how do you find the correct character?** There are a host of clever software programs for this that you can use or install, but often the simplest technique is to search online for, say, 'unicode degrees symbol'. That will show you several official unicode pages you can copy and paste from.

## Separating content and design

We could have started with this, because it's so important. The fundamental rule in multi-format editing is that **we separate content and design**.

For example, if our book includes an activity, some aspects of the activity belong to its content and some to its design.

- **Content**: a heading, instructions, a numbered list of tasks.
- **Design**: a surrounding box, a font change from the main text, the instructions in bold, decimal numbers used in the list.

In a different context, say on a small phone, we might use a completely different design that saves space and requires less processing power: a background colour rather than a box, the same font, instructions in italic, and whatever numbers are the default on the user's device.

The idea here is that:

- **Content** is up to the editor. It is constant (almost all the time).
- **Design** is up to the user and their viewport. It is format- and context-based.

In multi-format book production, then, we aim to create:

- One master version of all content.
- Any number of design stylesheets for different formats and contexts.

What does this mean for day-to-day editing? Here are some examples:

1. **Be on the lookout for subtle mixing up of content and design.** For instance, referring to the colours in a graph is risky: what if that graph appears in a black-and-white book? What if a reader is using a high-contrast display that changes colours?
2. **Avoid using design features for semantic purposes.** For instance, in a textbook don't write 'learn the words in bold', because in some viewports those words might appear italic, or pink, or highlighted instead. Rather say 'learn the words emphasised *like this*', and tag the phrase in the same way you'd tag a word to learn.
3. **Avoid positioning words** like 'above' and 'on the right'.

> ### Activity: A group stylesheet experiment
> 
> This is a quick activity to show how stylesheets work.
> 
> 1. In your group, ask two people to leave the room for five minutes.
> 2. Ask someone in the room to write their name on a sheet of flipchart paper. Given them a choice of coloured pens.
> 3. Ask someone else in the room to write down, on a separate piece of paper, instructions for how to recreate the exact design that was just created: the name on the flipchart paper. They are creating a design stylesheet.
> 4. Hide the original name, and get the first two people back into the room.
> 5. Give them the design instructions, and ask each of them to follow the instructions.
> 6. When they're done, compare their versions with the original. How good was the stylesheet?
{:.box}

## Naming design features

When you mark up a document, you will have to name the features of your book. For a given book, it's very important to establish early on what features it will include. For instance, each chapter might have:

- a list of learning objectives
- ten activities
- figures, each with a caption and a number
- a glossary
- a bibliography.

It is *very important* to set this list in stone early in a project, and to agree on the **exact name** you will use for each feature. And that name must describe the **purpose of the feature,** and not its design. That is, don't call a feature 'big red box' when you should call it 'key concept'.

In the simple list above, that's easy. But it can get complicated quickly. In a big textbook we worked on, we had to allow for a range of features, each with potential design features. Here is a selection of those features.

|         Element name         |                         Design preference                          |
|------------------------------|--------------------------------------------------------------------|
| Subheadline                  | Should look like second-level heading                              |
| Great-economists section     | Box, grey brackground, big heading                                 |
| How-economists-learn section | Box, grey background, big heading                                  |
| Videos                       | Embedded in main text on web; thumbnail and URL in margin in print |
| Questions                    | Red background, clickable on web                                   |
| Exercises                    | Red border, sans-serif text, caps heading                          |
| Figures                      | Any combo of images or tables, caption, reference, source          |
| Slideline                    | Clickable 'filmstrip' on web, figure with numbered steps in print  |
| Displayed maths              | Space before and after                                             |
| Sidenotes                    | Notes in the margin                                                |
| Footnotes                    | On web, these are popups, in print they are in the margin          |
| Definition boxes             | Popups on web, in margins in print                                 |

We discovered a short way into the project that team members had different ideas about what these features were called and how they were used. That set editing back severely. 

## Document trees

As you can tell by now, communicating with machines is about keeping things super organised. A well-organised document also has a clear and consistent tree-like structure. For example:

- **Chapter title** (`h1`)
    - *Section 1 heading* (`h2`)
      - Subsection 1.1 heading (`h3`)
      - Info box (`h3`)
    - *Section 2 heading* (`h2`)
      - Subsection 2.1 heading (`h3`)
      - Info box (`h3`)
      - Subsection 2.2 heading (`h3`)

As editors, we have to look out for the human tendency to break the tree structure because we're thinking visually.

For instance, our tree structure might require that our book's info-boxes have a third-level heading. Structurally, they are siblings of our subsections. But we want info-box headings to *look* less prominent than the subsection headings. We're tempted to give those boxes a fourth-level heading:

- **Chapter title** (`h1`)
    - *Section 1 heading* (`h2`)
      - Subsection 1.1 heading (`h3`)
        - Info box (`h4`)
    - *Section 2 heading* (`h2`)
      - Subsection 2.1 heading (`h3`)
        - Info box (`h4`)
      - Subsection 2.2 heading (`h3`)

But to a computer, and in terms of the tree structure here, those info boxes are now *children* of subsections 1.1 and 2.1, not siblings.

The real solution here is to use `h3` as the correct *content structure*, and to make those info-box headings look less prominent in our *design stylesheets*.

Maintaining a consisten tree structure is harder than it looks in theory. Keep your eyes peeled for broken tree structures in the documents you edit!

## Accuracy and consistency

That was a lot to take in. It only remains to highlight what you've already noticed: communicating with computers requires absolute accuracy and consistency.

As an editor, you're already the kind of person who loves accuracy and consistency, so you and computers should get along well. They will still test your patience often!

## Further reading

- [The Machine in Us/ing Us](https://www.youtube.com/watch?v=NLlGopyXT_g){:.show-url}, a video by Michael Wesch about how XML lets humans and machines 
- [Person in Lotus Position](9https://99percentinvisible.org/episode/person-lotus-position/){:.show-url}, a fun podcast from 99 Percent Invisible about adding new characters – and empjis in particular – to the Unicode character set.