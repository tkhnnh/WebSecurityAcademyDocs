Link: [DOM XSS in AngularJS expression with angle brackets and double quotes HTML-encoded](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-angularjs-expression)
Difficulty: Practitioner

# Action
Angular expressions are JavaScript-like code snippets used to bind dynamic data to HTML templates, primarily written within double curly braces  `{{ }}` or inside directive attributes.
Here is the payload:
```
{{$on.constructor('alert(1)')()}}
```

In javascript, every object has its own `constructor`,which refers to the constructor function that was used to create the object. This property is automatically created for every object, by the framework, and it can be accessed to determine the type or constructor function of an object.
The same goes for this function
- `$` Let's you know it's part of the framework and not user defined.
- `on` Method provided by the framework.
- `.constructor` `Property` of an object that refers to the constructor function that created the object.
- `()` Calls the newly created function.

Happy hacking!@#!@#
