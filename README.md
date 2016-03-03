# Template and templateUrl

## Overview

We've created a directive with a template - let's take a deeper look into that.

## Objectives

- Describe template and templateUrl
- Write a template using "template"
- Write a template using "templateUrl"

## Templates

You might've noticed that we've created a template item in our directive's object.

This will be put into the DOM where the directive is invoked.

Templates can only contain one root element! If we use more, Angular will error because it can't keep track of the elements properly.

```js
function MyDirective() {
	return {
		template: '<div>Hello world!</div>'
	};
}

angular
	.module('app')
	.directive('myDirective', MyDirective);
```

## templateUrl

To avoid our directives getting too big, we can also use `templateUrl` instead, pointing to a HTML file instead. This can be incredibly useful for any large directives.

```js
function MyDirective() {
	return {
		templateUrl: 'directive.html'
	};
}

angular
	.module('app')
	.directive('myDirective', MyDirective);
```

directive.html:

```html
<div>
	Wow, our directive in another file!
</div>
```

This would work the same as if we had it as a string in our directive - neat!