Keeping track of programming knowledge that I pick up each day.

#Git
* git checkout -: Checkout the last branch you had checked out.
* git fetch, git checkout <branch name>: Checkout a remote branch in your repository.

#Angular
* ngStrictDi: Enforce strict dependency injection through array syntax in your Angular apps.  This is particularly useful for ensuring your code doesn't break under minification.  Usage:
    * <div ng-app="myApp" ng-strict-di></div>
    * angular.bootstrap(elementToAttachTo, "myApp", {strictDi: true})

#JavaScript
* bind(context, ...args): Applied to a function, sets the functions "this" to be equal to context.  Prepends ...args as arguments to the function when it is called.  Usage:
    * myFunction.bind(null, "myParam")
      myFunction();
* String.slice(start, stop) vs. String.substring(start, stop):
    * If start > stop, substring will swap the two values where as slice will not.
    * If start or stop is negative or NaN in substring it will be treated as zero.
    * If start is negative in slice, it will start from the end of the string.
    * If stop is negative in slice, it will set stop to (string.length - 1) - Math.abs(stop).

##ES6
* Object Destructuring: in ES6 we no longer have to use dot notation to pull out the properties of an object that we want to use, instead we can do:
    let {prop} = obj;
And now prop will be equql to the prop property of object.  We can also do this with more than one property at once like so:
    let {prop1, prop2, prop3} = obj.
This syntax is much more concise and gives us a simple way to clean up code.

#CSS
* :nth-child(pattern): Pseudo class which applies to elements which are the nth child of their parent according to the pattern.  The pattern can simply be a number or can be more complex such as "n + 2".  The childrens index starts at 1.  Usage:
    * :nth-child(n + 2):nth-child(-n + 3) - Selects all elements from the second up until the third to last.
* pointer-events: none | visible | painted...: Property which specifies when a particular element should respond to mouse events.  Setting to "none" comes in handy when you have an element which does not have any click functionality overlapping an element which does.  It will allow the underlying element to handle the click even if the overlapping element is clicked.