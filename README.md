Keeping track of programming knowledge that I pick up each day.

#Git
* git checkout -: Checkout the last branch you had checked out.
* git fetch, git checkout <branch name>: Checkout a remote branch in your repository.
* git reset --hard HEAD: throw away any changes you have made and reset to the head of the current branch you are on.
* git push origin --delete <branch name>: Delete a remote git branch.
* git remote prune origin: Prune stale, unreachable branches from your local repo.
* Git Hooks: Git hooks allow you to run a script before or after specific git events.  Some events you can hook into are post-update, pre-commit, pre-push, pre-rebase, and pre-applypatch.  Hooks are stored in the .git/hooks folder of your local repo and are not tracked by git.  In addition to these local hooks, there are also the pre-receive, update, and post-receive hooks which live on the server.
* git rebase -i ~HEAD(x): Can be used to squash the last x commits together into one.  This is useful if you have many commits on a certain branch but want to make your history more concise.  Squashing commits will combine the changes from several commits into one to keep your history readable.
* Git attributes: Allow you to apply specific merge functions, filter functions, and diff flags to a certain file or glob.  Attributes:
    * filter=myFilterFunc, where myFilterFunc handles the clean and/or smudge functions
    * merge=myMergeFunc, where my merge specifies how to merge the file such as taking only ours changes.
    * -diff (binary diff flag)
* Git config: there are three places that git will look for a config file, ~/.gitconfig, $GIT_DIR/config, and $(prefix)/git/config.  The order of precedence goes from global to local so the config in your $GIT_DIR will take the highest precedence.  Git config files are not in a location that can be tracked and used automatically, this is for security reasons.  Each user of a repo will have to manually setup their config file or reference an example config that is tracked.

#Angular
* ngStrictDi: Enforce strict dependency injection through array syntax in your Angular apps.  This is particularly useful for ensuring your code doesn't break under minification.  Usage:
    * <div ng-app="myApp" ng-strict-di></div>
    * angular.bootstrap(elementToAttachTo, "myApp", {strictDi: true})
* angular.bootstrap(elementToAttachTo, "myApp"): Used to manually bootstrap Angular applications without explicitly attaching ng-app to any DOM element.  It can also be used to declare two ng-apps on one page.  There can only be one explicit ng-app attached to a DOM element on a page but you can manually bootstrap an Angular app to any number of elements.
* $emit() vs. $broadcast(): Emit and broadcast are the two ways you can fire events in Angular.  The difference is that emit will only notify $rootScope listeners while broadcast will start by notifying $rootScope listeners and fanning the event out to all of the children of $rootScope.  This makes emit a more efficient choice in some cases.

#React
* this.setState(stateObj): Used to update the state of a component.  This will trigger a render() which will then update the display of the component if there are differences between the DOM and shadow DOM.

#Webpack
* file-loader: A Webpack loader that can be used to include static asset files such as images or fonts in your bundle.

#JavaScript
* bind(context, ...args): Applied to a function, sets the functions "this" to be equal to context.  Prepends ...args as arguments to the function when it is called.  Usage:
    * myFunction.bind(null, "myParam")
      myFunction();
* String.slice(start, stop) vs. String.substring(start, stop):
    * If start > stop, substring will swap the two values where as slice will not.
    * If start or stop is negative or NaN in substring it will be treated as zero.
    * If start is negative in slice, it will start from the end of the string.
    * If stop is negative in slice, it will set stop to (string.length - 1) - Math.abs(stop).
* Array.map(fn): Applies fn to each element of the array, returns the new array with fn(Array[n]) for each element n in the original array.
* Array.filter(fn): Runs fn on each argument in the array, removing the elements for which fn(array[n]) returns false and creating a new array.
* Truthy vs. falsey: Javascript expressions evaluate to truthy or falsey which can then be used to determine the branch taken in the code.  Since there are only six falsey values in Javascript (undefined, null, NaN, 0, "", and false) the best way to test for truthiness is to test for not falseyness.  Objects always evaluate to truthy so you have to be careful for odd examples like 'new Number(0)' and 'new Boolean(false)' which both evaluate to truthy.
* Native DOM node removal: if you need to remove an element from the DOM without the help of jQuery, you can use:
    let nodeToRemove = document.getElementById('myId');
    nodeToRemove.parentNode.removeChild(nodeToRemove)

##ES6
* Object Destructuring: in ES6 we no longer have to use dot notation to pull out the properties of an object that we want to use, instead we can do:
    let {prop} = obj;
And now prop will be equql to the prop property of object.  We can also do this with more than one property at once like so:
    let {prop1, prop2, prop3} = obj.
This syntax is much more concise and gives us a simple way to clean up code.  Object destructuring can also take a default argument in case the value is undefined on the object:
    let {prop1 = 10} = obj
* let: Variables declared with let are bracket scoped as opposed to variables declared with var which are functionally scoped.
* const: Variables declared with const are also bracket scoped but in addition they can only be written to once otherwise they will throw an error.
* Object.assign(target, ...sources): Used to copy the values of all own enumerable properties from the sources objects to the target, returns the new target object.  Uses the Get of sources and Put of target. 
* Template strings: 'Hello ${worldVar}'.  The variable or expression inside ${} will be replaced with the result of the toString() method called on it.
* Mulitline Strings: Using backtick string notation, ES6 supports multiline strings which will evaluate to include the newline character and any extra tabbing.
* Arrow functions: (input) => { //code in here }.  A concise way to represent functions, especially when used inline or in combination with map, filter, reduce.  Arrow functions also share their this with their parent.
* for-of loop: The for of loop is new to Javascript in ES6 and loops over an iterable assigning each enumerated item while looping.  You can convert data structures to iterablea using the entries(), keys(), or values() functions.  Example:
    let x = [1, 2, 3];
    for (let item of x.entries()) {
        console.log(item)
    }

#NPM
*shrinkwrap: Run using "npm shrinkwrap --dev".  This will create a npm-shrinkwrap.json file which will be used to resolve all of the npm dependencies and sub-dependencies in your package.json.  This can prevent unwanted and breaking updates to packages that can come through the use of the ~, ^, and * modifiers in your package.json and the package.json of any of your dependencies.  

#CSS
* :nth-child(pattern): Pseudo class which applies to elements which are the nth child of their parent according to the pattern.  The pattern can simply be a number or can be more complex such as "n + 2".  The childrens index starts at 1.  Usage:
    * :nth-child(n + 2):nth-child(-n + 3) - Selects all elements from the second up until the third to last.
* pointer-events: none | visible | painted...: Property which specifies when a particular element should respond to mouse events.  Setting to "none" comes in handy when you have an element which does not have any click functionality overlapping an element which does.  It will allow the underlying element to handle the click even if the overlapping element is clicked.
* calc(expression): Calc will set values for attributes such as height and width to the result of expression.  Expression can use +, -, *, / as well as percentage and pixel values.  This can be useful to take into account percentage and pixels such as:
    .class-name { 
        height: calc(20% + 10px);
    }
* css-modules: This npm package can be used to create locally scoped css and remove the need for systems like BEM that were needed to overcome the difficulties of CSS being globally scoped.  A set of styles can be included in your JavaScript component using "let styles = import './mystyles.css';".  Then in your tenplates the CSS class can be injected using "styles.myClassName".  css-modules will generate a unique class name for your component that will prevent naming conflicts.

#HTML
* script - async and defer:  By default, the DOM parser will load script tags synchronously.  This means that if you have a script tag that takes abnormally long to fetch, the rest of the page that comes after your script tag will not load until the tag is fetched and parsed.  Adding async to the script tag will allow the parser to continue parsing the rest of the page and handle the script tag once it is fetched.  The defer tag will also allow the page to continue parsing and then will process the script once the DOM parsing is completed.  However, if you have a document.write call inside the loading script, the page could render incorrectly if you use async or defer.

#Regular Expressions
####Regular expressions can be used to verify that strings match a certain pattern.  One useful application is input validation.  
* ?: Denotes that the previous expression is optional
* \character: represents the literal of the character
* {n, k}: Denotes that between n and k repetitions of the previous expression are allowed
* [1-9]: Any number between 1 and 9 is allowed
* | : Marks alternate possibilities that are allowed

#Chrome Dev Tools
*Blackboxing: If you navigate to Dev Tools > Settings > Blackboxing you will be able to add URI patterns for files to be blackboxed.  This will prevent chrome from outputting information about the internals of the file.  One use case is if you have a custom logger and all of your logging line numbers are listed as coming from inside the logger.  If you blackbox the logger script you will see the line numbers displayed as what line the custom logger was cqlled from, which is usually more useful.