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
  1. [Syntax] (#syntax)
    1. [Components] (#components)
    1. [Descendants] (#descendants)
    1. [Modifiers] (#modifiers)
    1. [States] (#states)

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

## Syntax

Syntax: `<componentName>[--modifierName|-descendantName]`

Component driven development offers several benefits when reading and writing HTML and CSS:

* It helps to distinguish between the classes for the root of the component, descendant elements, and modifications.
* It keeps the specificity of selectors low.
* It helps to decouple presentation semantics from document semantics.

You can think of components as custom elements that enclose specific semantics, styling, and behaviour.

### Components 

Syntax: `componentName`

The component's name must be written in camel case.

```css
.myComponent {
  font-size: 20px;
}
```

```html
<article class="myComponent"></article>
```

### Descendants

Syntax: `componentName-descendantName`

A component descendant is a class that is attached to a descendant node of a component. It's responsible for applying presentation directly to the descendant on behalf of a particular component. Descendant names must be written in camel case.

```html
<article class="tweet">
  <header class="tweet-header">
    <img class="tweet-avatar" src="{$src}" alt="{$alt}">
    …
  </header>
  <div class="tweet-body">
    …
  </div>
</article>
```

### Modifiers

Syntax: `componentName--modifierName`

A component modifier is a class that modifies the presentation of the base component in some form. Modifier names must be written in camel case and be separated from the component name by two hyphens. The class should be included in the HTML _in addition_ to the base component class.

```css
.btn {
  padding: 20px 10px;
}

.btn--primary { 
  background: rgb(148,146,231);
}
```

```html
<button class="btn btn--primary">…</button>
```

### States

Syntax: `componentName.is-stateOfComponent`

Use `is-stateName` for state-based modifications of components. The state name must be Camel case. **Never style these classes directly; they should always be used as an adjoining class.**

JS can add/remove these classes. This means that the same state names can be used in multiple contexts, but every component must define its own styles for the state (as they are scoped to the component).

```css
.tweet { 
  height: 90px;
}

.tweet.is-expanded { 
  height: 200px;
}
```

```html
<article class="tweet is-expanded"></article>
```

## License

[MIT](https://github.com/grvcoelho/css/blob/master/LICENSE) &copy; 2015
