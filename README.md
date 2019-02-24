# Highlighter.js

Easily extend any HTML page for custom highlighting.

Highlighter.js is a vanilla JavaScript library that provides a simple API for highlighting HTML pages. Developers can save the highlighted references as JSON and render them in the future. Save the highlights to:

- Learn what parts of your writing users are reading and resonating with
- Crowdsource annotations and display them in context
- Identify which parts of a text are most important to your users

## Features

Highlighter.js provides these important features:

- Re-render annotations stored in JSON.
- Highlighting works even on lines that span multiple nested DOM elements or multiple sibling elements.
- Flexible callbacks for a variety of purposes, such as sharing quotations on [Twitter](https://vingkan.github.io/highlighterjs/social.html)

Other related open source libraries include:

- [anythingcodes/highlight-share](https://github.com/anythingcodes/highlight-share)
- [720kb/highlighter.js](https://github.com/720kb/highlighter.js)

## Installation

Include one of the these two JavaScript files in your application:

```html
<script type="text/javascript" src="highlighter.js"></script>
<script type="text/javascript" src="highlighter.min.js"></script>
```

## API

Get an instance of `Highlighter`. Pass a DOM element to give highlighting capabilities to that container. Optionally, provide a class name to apply to all highlighted lines. By default, they will have the class `"is-highlighted"`.

```javascript
const hl = Highlighter(document.getElementById("text"), className);
```

Bind a callback function to run whenever the user highlights some text and clicks the highlight tooltip.

```javascript
hl.onHighlight(callback);
```

The callback provides a single argument, a highlighter object with the following fields:

```javascript
{
    start: 546, // start index of highlighted in the container text
    end: 613, // end index of highlighted in the container text
    el: {}, // reference to DOM element that was highlighted, ignore when storing data
    text: "HackIllinois 2019 is a great event...", // text that was highlighted
    timestamp: 1551022816360 // local time of highlight in milliseconds
}
```

Pass a single highlight object or an array of highlight objects to render them in the container.

```javascript
hl.renderHighlights(highlights);
```

Remove all highlighted lines.

```javascript
hl.removeHighlights();
```

Get an array of all highlighter objects currently rendered.

```javascript
hl.getHighlights();
```
