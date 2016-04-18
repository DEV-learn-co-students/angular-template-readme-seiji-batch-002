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

This is okay:

```html
<div>
	Woo our directive goes here!
</div>
```

This will not work:

```html
<div>
	Woo our directive goes here!
</div>
<span>What about here - oh no!</span>
```
## templateUrl

As our templates get more complex, they can become difficult to read inside of our controller function. In the example below, we're saving each line of our template as a seperate element in an array, then joining the elements together. 

```js
function MyDirective() {
	return {
		template: [
        '<div class="dropdown">',
			'<button class="dropdown__title">',
				'Options',
			'</button>',
			'<ul class="dropdown__list">',
				'<li class="dropdown__item">',
					'<a class="dropdown__link" href="#">',
						'Edit',
					'</a>',
				'</li>',
				'<li class="dropdown__item">',
					'<a class="dropdown__link" href="#">',
						'Transfer',
					'</a>',
				'</li>',
				'<li class="dropdown__item">',
					'<a class="dropdown__link dropdown__link--delete" href="#">',
						'Delete',
					'</a>',
				'</li>',
			'</ul>',
        '</div>'
      ].join('')
	};
}

angular
	.module('app')
	.directive('myDirective', MyDirective);
```

To avoid our directives getting too big like above, we can also use `templateUrl` instead, pointing to a HTML file instead. This can be incredibly useful for any large directives.

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

This would work the same as if we had it as a string in our directive - neat! Normally we'd store our views in a folder inside our module folder `js/moduleName` inside a folder named `views`. This keeps everything all together!

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/angular-template-readme'>Angular Template</a> on Learn.co and start learning to code for free.</p>
