# MOAR Elements

These mixins were originally based on their better known ancestor LESS Elements (at <http://lesselements.com>), but they are
a set of useful mixins for LESS, the CSS pre-processor (<http://lesscss.org>).

Due to the lack of organization and frequency of updates of its ancestor, I decided to fork to a cleaner version of the codebase.


## How to Contribute

1. fork the project and submit pull requests
2. submit issues
3. edit the wiki
4. message me directly

I am by no means an expert at LESS mixins, but I will try my best to keep this as up to date as possible. I would like this toolset to be as feature-rich as possible, but it can only get better with your help.


## Rules for Contributing Code
The original LESS Elements code was cluttered and inconsistent with mixin definitions.  This repository need a bit of consistency
to make it easier to read, easier to use, and easier to maintain/update. The rules are as follows:


### Vendor-Prefix Wrappers
Though the names are different, the functionality (and arity) of the CSS properties should be exactly the same as the mixin.

* **Wrappers should pass their arguments directly to the vendor-prefixed counterparts.**
  * These properties ALL accept the same values.
  * There's no need to ask for them explicitly in the mixin definition.


#### .border-radius example
```
.border-radius(...) {
  -webkit-border-radius: @arguments;
     -moz-border-radius: @arguments;
          border-radius: @arguments;
}//.border-radius
```

CSS `border-radius` accpets up to four arguments (top-left, top-right, bottom-right, bottom-left) starting with the top-**LEFT** corner.  It's wrapper should do the same.  

With the `...` argument in the mixin definition, any argument passed to `.border-radius` will be passed along to the vendor-prefixed counterparts. See "Advanced arguments and the @rest variable" at <http://www.lesscss.org/#-parametric-mixins>.


#### Property Value Alignment
```
.border-radius(...) {
  -webkit-border-radius: @arguments;
     -moz-border-radius: @arguments;
          border-radius: @arguments;
}//.border-radius
```
You might have noticed that all of the `@arguments` in `.border-radius` are aligned.  This is preferred for vendor-prefix wrappers as it makes it easier to update how arguments are passed if they need to be changed.


#### Closing Comments
```
.border-radius(...) {
  -webkit-border-radius: @arguments;
     -moz-border-radius: @arguments;
          border-radius: @arguments;
}//.border-radius
```
Closing comments are highly recommended to preserve readability with long blocks. An example can be seen above (`//.border-radius`).


### Custom Mixins
Custom mixins are those that do not purely wrap vendor-prefixed properties.  These mixins may accept arguments, but there are a few rules
for arguments.

1. Required arguments ALWAYS go first.
	
	Optional arguments go AFTER required arguments.  *If an optional argument is defined before a required argument, it's not really optional, is it?*
	
2. Use semicolons (;) to separate arguments. 
	
	See "Mixins With Multiple Parameters" at <http://lesscss.org/features/#mixins-parametric-feature-mixins-with-multiple-parameters>
	
3. Always put a semicolon after the last argument.

	`.my_mixin(@arg1:val;)`


## Request for Feedback
Oreolek was mentioned to have a namespaced fork of the original LESS Elements codebase where the mixins are provided under a hash-namespace (nested mixins, so to speak). I would like to do the same with MOAR Elements, but I need your feedback to determine the best way to namespace these mixins.


## License
This work is dedicated to the public domain and is free for all uses, commercial or otherwise. No form of credit required.
