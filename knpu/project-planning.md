## JavaScript Project

Premise: A spot where developers can come to get tough. Entering in # of
reps of weight and climbing up a leaderboard.

### Starting Project

Start with a basic design and:

* working registration
* non-JavaScript page where we can enter reps (units include, lbs, kg, cats, etc)
* non-JavaScript leaderboard

### Building

#### 1) Bower: Setup

- Added the .bowerrc file
- bower init

#### 1) Bower: Install Bootstrap and jQuery

- bower install bootstrap --save
- ignored web/assets/vendor in gitignore

#### 2) Include them in the base template

#### 3) Rep Form: AJAX Submit

- using .preventDefault()
- using document.ready

#### 4) Rep Form: Installing FOSRestBundle

- comp require friendsofsymfony/rest-bundle ~1.2.2
- comp require jms/serializer-bundle ~0.13.0

#### 5) Form: JSON Form Response

#### 6) Form: Handling client-side errors

#### 7) Form: Adding error highlights

#### 8) Form: Show a notification on save

#### 9) Form: Handling success with a message

- yet more custom code for our errors messaging spot
Problems:
- the errorList thing is redundtant and a disaster
- a lot of work to handle parsing through Symfony errors and fields
- all this stuff is inline
Solutions:
- generic error list object
- centralized parsing of Symfony error responses
- get this into its own little module

#### 10) Form: Refactoring into simple object

- not really helpping yet, one gigantic object
- differences between objects and hashes? :)

#### 11) Form: Adding more methods to the object

- forced to pass $form into the function
- forced to re-look up for errorList
- referring to repForm, not this

#### 12) Form: Instantiated object

- created the construct function
- instantiated the guy

#### 13) Form: Tweak methods in object

- used $.proxy so we could get "this"
- used self later to keep this

#### 14) Form: Isolate to an external file

- using self-executing function
- seeing an alias for undefined
- still need to include the script file manually

#### 15) Form: Isolate Symfony error processing

- this returns an object, not even a function that acts as constructor
- order including the script files is important
- need to pass it into self-executing function

### 16) Form: Create Error List Utility

- Moved creation of the ul error list into JavaScript
- New ErrorList object has an easy API

#### 17) Leaderboard: Install dustjs

- bower install  dustjs-linkedin --save

#### 18) External object to start rendering leaderboard

- rendered template just inside a script tag and passed it in
- nothing too special at this stage

#### 19) Rendering leaderboard template

- rendering data into twig via {{ leaders|json_encode|raw }}
- compiling and rendering the Dustjs template
- passing in "dust" into self-executing block
- once again using self = this;

#### 20) Install FOSJsRoutingBundle

- comp require "friendsofsymfony/jsrouting-bundle" "@stable"

#### 21) Leaderboard: Reloading Leaderboard via AJAX

- using a delegate selector for a js- button
- using $.proxy on the callback
- using Routing.generate for the first time
- adding a button in the dust template

#### 22) Leaderboard: Using promises to add a fade

- using promises - attaching to success and triggering failure at least

#### 23) Leaderboard: EventEmitter to load on new reps

- bower install eventEmitter
- create a global event emitter
- use DI to push it into the objects
- add a listener and trigger an event

11) On hover of .username-info elements, let's pop up a cute-box
* jQuery plugin
* Routing.generate, but we could set that on some global config in Core
to make this plugin even more re-usable

12) On homepage, include the leaderboard
* breaks because no leaderboard object
* breaks again because no Messaging object

13) Introduce RequireJS
* basic setup
* roll out to each page

14) RequireJS Optimizer
* do we move assets out of web?

15) Grunt
* move in RequireJS
* add in jshint
* add in css-min

15.5) Dust Template compiling

16) Less/Sass extra credit?
* add watch task

17) Refactor entry into AngularJS

3) Add another form field after submitting
* introduce delegate events

### Questions

- what is the bower.json ignore section?


### Random Notes

- you don't need "script type="
- what is document.ready really?
- we could also make a FormErrorHighlighter around step 17 to make the
  error decorating of form fields automatic