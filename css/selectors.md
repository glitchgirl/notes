# Selectors

## Strength

MOST
Type selectors (e.g., h1) and pseudo-elements (e.g., ::before).
Class selectors (e.g., .example), attributes selectors (e.g., [type="radio"]) and pseudo-classes (e.g., :hover).
ID selectors (e.g., #example).
LEAST

## Types

`*{}`
Selects all elements

`p{}`
Selects all `<p>` elements

`div, p{}`
Selects all `<div>` elements and all `<p>` elements

`div p{}`
Selects all `<p>` elements inside `<div>` elements

`div > p{}`
Selects all `<p>`elements where the parent is a`<div>` element

`div + p{}`
Selects all `<p>` elements that are placed immediately after `<div>` elements

`p ~ ul{}`
Selects every `<ul>` element that are preceded by a `<p>` element

[target]
Selects all elements with a target attribute
