# css

*Opinionated CSS styleguide for scalable applications*

## Table of Contents

  1. [Terminology](#terminology)
    1. [Rule Declaration](#rule-declaration)
    1. [Selectors](#selectors)
    1. [Properties](#properties)
  1. [Formatting] (#formatting)
    1. [Spacing] (#spacing)
    2. [Quotes] (#quotes)
    3. [Comments] (#comments)

## Terminology

The following are some terms used throughout this styleguide.

### Rule declaration

A “rule declaration” is the name given to a selector (or a group of selectors) with an accompanying group of properties. Here's an example:

```css
.avatar {
  font-size: 18px;
  line-height: 1.2;
}
```

### Selectors

In a rule declaration, “selectors” are the bits that determine which elements in the DOM tree will be styled by the defined properties. Selectors can match HTML elements, as well as an element's class, ID, or any of its attributes. Here are some examples of selectors:

```css
.avatar {
  font-size: 20px;
}

#id {
  font-size: 20px;
}
```

### Properties

Finally, properties are what give the selected elements of a rule declaration their style. Properties are key-value pairs, and a rule declaration can contain one or more property declarations. Property declarations look like this:

```css
.avatar {
  background: #f1f1f1;
  color: #333;
}
```

## Formatting

The following are some high level page formatting style rules.

### Spacing

CSS rules should be comma separated and leave on a new line:

```css
/* wrong */
.avatar, .tweet {

}
```

```css
/* right */
.avatar, 
.tweet {

}
```

Properties should use a space after `:` but not before:

```css
/* wrong */
.avatar {
  font-size : 12px;
}

.tweet {
  font-size:12px;
}
```

```css
/* right */
.avatar {
  font-size: 12px;
}
```


Rule declarations should have one property per line:

```css
/* wrong */
.avatar {
  font-size: 12px; letter-spacing: 2px;
}
```

```css
/* right */
.avatar {
  font-size: 12px; 
  letter-spacing: 2px;
}
```

Declaration should be separated by two new lines:

```css
/* wrong */
.avatar {
  font-size: 12px;
}
.tweet {
  letter-spacing: 2px;
}
```

```css
/* right */
.avatar {
  font-size: 12px;
}

.tweet {
  letter-spacing: 2px;
}
```

### Quotes

Quotes are optional in CSS. You should use single quotes as it is visually clearer that the string is not a selector or a style property.

```css
/* wrong */
.avatar {
  background-image: url('/img/you.jpg');
  font-family: 'Helvetica Neue Light', Helvetica Neue, Helvetica, Arial;
}
```

```css
/* right */
.avatar {
  background-image: url(/img/you.jpg);
  font-family: Helvetica Neue Light, Helvetica Neue, Helvetica, Arial;
}
```

### Comments

Avoid comments as hard as you can. Comments are not easily mantainable and are usually used to supress application design mistakes. Leave comments only to things that are **really** not straightforward such as browser-specific hacks. Put comments on their own lines to describe content below them.

```css
/* wrong */
.avatar {
  height: 200px; /* this is the height of the container*/
  background-color: red; /* brand color */
}
```

```css
/* right */
.avatar {
  height: 20px;
  
  /* this is a hack to fix click behavior on Safari 6.0 */
  pointer-events: none;
}
```

## License

[MIT](https://github.com/grvcoelho/css/blob/master/LICENSE) &copy; 2015
