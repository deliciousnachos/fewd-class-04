# The Box Model!

### Learning Objectives

- Construct a CSS rule using selectors, declarations, properties, and values
- Demonstrate the use of class and ID selectors to target specific element(s)
- Identify the components of the box model
- Use display properties to determine how an element is displayed on the page


### Sidebar: HTML5 Semantic Elements

The new(ish) HTML5 spec allows us to use "semantic elements". Semantic elements are named in such a way that clearly explains their purpose to the developer and the browser. They're helpful for SEO and accessibility. Some semantic elements worth mentioning include `<header>`, `<nav>`, `<footer>`, `<main>`, `<article>`, and `<aside>`.

- Suggested reading: [W3Schools page on Semantic Elements](https://www.w3schools.com/html/html5_semantic_elements.asp)

## Including CSS

Most commonly, you'll be including CSS in the head of your HTML file, like so:

```html
<!DOCTYPE html>
<html lang='en'>
<head>
  <meta charset='UTF-8' />
  <meta name='viewport' content='width=device-width, initial-scale=1.0' />
  <meta http-equiv='X-UA-Compatible' content='ie=edge' />
  <title>CSS Demo</title>
  <!-- Here is our CSS inclusion -->
  <link rel='stylesheet' type='text/css' href='./style/style.css'>
</head>
```

You may also see CSS written in the actual head tags of the document, or inline on elements themselves. Ideally, you shouldn't be doing either of those things; keep your styles contained.

Additionally, when you're including CSS files in the head of the HTML file, the order matters. If you put `reset.css` after `style.css`, the rules in `reset.css` will override the rules in `style.css`.

# Selectors & Specificity

There are multiple ways to target elements. We will be going over some of the most common ways today, and talk about a few others later. In order from least to most specific:

- Element selectors
- Class selectors
- ID selectors

#### References

- [Here is the W3CSchools documentation for selectors](https://www.w3schools.com/cssref/css_selectors.asp)
- [Please don't think you have to memorize all of these, I have had the site bookmarked for 6 years and still look at it weekly](https://code.tutsplus.com/tutorials/the-30-css-selectors-you-must-memorize--net-16048)

## 🚀 Lab: Open up the `tags-boxes/index.html` file and follow along!!

## Sidebar 2: `reset.css`

When you're including CSS in your HTML, you'll most commonly be linking a `style.css` file. You should also include [`reset.css`](http://meyerweb.com/eric/tools/css/reset/reset.css). `reset.css` is a stylesheet that strips out all the browser defaults from our CSS and leaves us free to do whatever we want.

## 🚀 Mini-Lab: Let's add a `reset.css` to our tags & boxes file!

# The Box Model!

One of the tricky things about CSS at first is the Box Model. But it's actually really simple. Let's break it down.

![](https://dl.dropboxusercontent.com/s/capg35hblhr6o7v/Screenshot%202015-10-13%2014.11.39.png?dl=0)

Any HTML element can be considered a box, and so the box model applies to all HTML elements. If you select an element and ascribe it a height and width, the content itself will be that height and width.

What the size doesn't include:
- padding
- border
- margin

So, in practical terms, this means that if you have two elements with a width of 50%, they won't fit side by side if you give them borders and padding.

In `index.html`:

```html
<p>This is a paragraph</p>
<p class='padding'>This is a paragraph</p>
```

In `style.css`:

```css
p {
  color: blue; /* already in your file */
  font-size: 2em; /* already in your file */
  width: 20%; /* this line should be new */
}
```

Let's check this out in our chrome browser with the developer tools. As you can see, everything is identical. Let's go ahead and add some padding to the html element with class "padding". In `style.css`:

```css
.padding {
  padding: 10px;
}
```

Even though the width in the CSS is the same, the element with padding is larger.

All these different sizings can be confusing. This can especially be frustrating when you think something's 20% when in actuality it isn't.  

When you find yourself adding both width and padding to an element, it's a pretty good rule of thumb to immediately just add the declaration `box-sizing: border-box;` to your declaration box. The `box-sizing` property does about what it sounds like it does: set how the browser calculates the width of the box. And the `border-box` value tells the browser to look at the _border_, not the _content_. (The default value for `box-sizing` is `content-box`.)

# Display

Astonishingly, the display property has to do with the way an element _displays_ on the page. Who would have guessed?

`display` is one of the most important properties for creating layouts. Every element has a default display value, based on what type of element it is.

#### Block

`div`, `p`, `h1`-`h6`, and semantic HTML5 elements have a default `display` value of `block`. A `block` element starts on a new line. Block elements have margin, padding, and borders, and can have a height and width. Block elements will not naturally display on the same line.

#### Inline

`span` and `a` elements have a default `display` value of `block`. This means they can be inserted into a block-level element and not disrupt the flow of the element's contents (for example, links in content do not need to be on their own lines). While padding and margin can be applied to all sides of an `inline` element, only the padding/margin on the left and right will affect the surrounding content. They also cannot have a width and a height.

#### Inline-block

`inline-block` is the unholy marriage of `block` and `inline`. Elements with `display: inline-block;` can accept padding, margin, height, and width, but will naturally line up on the same line. [Here's a more in-depth look at `inline-block`](https://designshack.net/articles/css/whats-the-deal-with-display-inline-block/).

#### None

As one might expect, `display: none;` totally hides the element -- it's as if it didn't exist.

#### Other display values

You'll also see these in the wild:
- `table`
- `flex`
- `grid`

We'll talk about `flex` in Unit 2; you shouldn't have to use `table` much ever; and `grid` is still pretty new.

### 🚀 Practice! 

Use `inline-block` to add more padding to the `code` elements in the tag options. If you get done with that, make all the display properties at the end all line up!

