Svelte: the easy onramp into web programming for dynamic applications


It's a web framework that compiles into pretty much vanilla JS HTML CSS
- actually not just a javascript framework, compiles into all three


```diff
+ Less code needed than other frameworks
+ no virtual DOM like in react (doesn't need it)
+ reactivity out of the box
```

less boilerplate code

{} inline framework

#### [[virtual dom]]

#### Reactivity:
when something changes supports reactions to changes instantly 
- - $: syntax

[[Svelte vs React]]


- coding done in .svelte files

script JS code at the top as normal

in HTML, we can use {} to write JS code inline
- interpolation, reactivity
- nothing special about variable declarations, no need to mark as stateful etc. just traditional JS that becomes ractive in the code


create normal variables using let and use them reactively with {} syntax in the code.

Primary reason we picked it is that it's very easy to learn for new developers, especially


Svelte supports small components best

speed


[[Svelte Stores]]


Svelte files have, like a normal HTML file,

```html
<script> tag

<style> tag -- importantly, style tags in blocks are scoped to components alone

<template> blocks

```

haha in essence it's pretty cool


