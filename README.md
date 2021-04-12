# The Ultimate React Checklist

The world of Javascript and React is so open and wide, it's easy to get lost.

But when you get lost in the world of React, you take with you all your peers who would be reviewing the code.

  
To save everyone's time and effort, all we gotta do is think of '**pushing the code**' as '**going on a trip**'.

What do we do before we finish packing? ----  _**We make a checklist of all the important stuff that we need.**_

That's exactly what we are gonna do before pushing our code.  
  
Benefits you ask?

Well, a little trouble while writing a code will result in big savings in the long run.  
It would not just improve code quality because of reviews being easier to perform, but save a lot of reviewer's time as well.

### So let's dive in!

# **Overview:**

-  ### Do not push the entire code at once
        
      Nothing breaks a developer's reviewing spirit more than seeing 1000 lines of code to be reviewed at once!
      
      Like they say  _**"Ask a programmer to review 10 lines of code, he'll find 10 issues. Ask him to do 500 lines and he'll say it looks good."**_
      
      Please do not subject your peers to this hardship!
        

-  ### Make sure the feature you are pushing actually works
        
      There's no point in reviewing a half-written code that'd change the very next day. So whenever you push a code, make sure that particular functionality is completed as per the current requirements, and then when the requirement changes, let your team know so they can make out the changes.
        
- ### Try not to mix your component types (Prefer hooks)
        
     Try to stick to one style of writing components. You don't want that disappointment when your teammate comes to you with an amazing new hook that solves your problem only to find out that you can't use it since you were writing class components.
     
     Try to write functional components with hooks so as to simplify your code and get rid of this, like literally  **this** (the keyword - see what I did there? ah? ah? PUN)
        
- ### Separate out JS and JSX
        
     Put all the code that requires, let's call it, 'react stuff' in JSX file and put any logic like data massaging, constants, utility functions in a JS file. Make your JS files in such a way that they return stuff that you expect, then have your states updated on the JSX file.
     
     This will enable your peers to know exactly how that function works and what it returns. Moreover, when you mess up in your JSX, this function you wrote in JS is won't suffer for JSX's mistakes since it would be independent.
     
     Moreover, you can push your code function by function or service by service.
        
- ### DRY - Don't Repeat Yourself
        
     See a piece of code or similar logic repeating more than twice? Well, you shouldn't.
     Try to group them up and dump them in a file so that they can be reused.
        
- ### Name your files properly
        
     Do not become one string banjo while naming your files and go camelCase or PascalCase for everything. Use PascalCase with your JSX and go camelCase with your JS files
        
- ### Follow linting rules unless you have a very well-defined reason not to
        
     React linters like ESLint define a well accepted way of writing code which not only makes your code look pretty but also helps it keep simple for others to understand. Unless you can backup your claim with a good enough reasoning and research, always stick to what ESLint says.
     
     You can also use SonarLint to get rid of any issues that Sonar may report later, if your team is using that.
        
- ### Specify a doctype in index.html
        
     Specifying a doctype will make your application follow the standards set by that doctype and won't trigger  **quirk mode**  that could lead to unexpected behaviour
        

----------

  

# **Javascript:**

- ### Use the new ECMAScript features as per your transpiler - And use at least ES6
        
     JS is an everchanging world and each year it brings with it a bunch of cool stuff for you to play with. If your transpiler supports the latest version of JS, not using the new features of ECMAScript is just handicapping yourself.
     
     Since all major browsers support ES6 even with a relatively older version, it's a safe bet to use (but still depends on your use-case)
        
 -   ### Destructure your objects and arrays
        
	    There's nothing more infuriating that seeing a code like this:
	    `const a = response.data.payload.val1`
        `const b = response.data.payload.val2`
        `const c = response.data.payload.val3`
        
        
        Please destructure your objects so all you use is val1, val2, val3. It removes all those cluttering, prevents typos and makes the code much more readable.
        
   -   ### Use spread operator
        
        Copying an array? - Use spread operator
        Creating a new object from two other objects?  - Use spread operator
        Concating arrays?  - You guessed it.... Use spread operator
        
  -   ### Swap out your  _var_  with  _let_  and  _const_

      Define proper scopes of your variables instead of giving them free reign over the code.

  -   ### Use arrow functions

      Do not attempt to deal with the headache of bind, go instead for arrow function and let it do the binding for you.
        

----------

  

# **React:**

-    ### Don't use div just for wrapping multiple children, use React Fragment instead
        
        Fragments prevent an extra node to the dom. It may not seem like any significant change in a single place but it accounts for a lot when you see across the entire project.
        
        Like they say '_**A code's performance dies by a thousand cuts**_'.
        
  -   ### Use StrictMode for React

      StrictMode activates additional checks and warning for your application so that you can fix it. And since it only performs checks in the development environment and does not impact production build, it's safe to use it.

  -   ### Split your bundles

      Instead of bundling together all the files at once, consider splitting them so you only ship the files that are needed to display the content the user is viewing.

      **React.lazy**  does it for you. For example - wrap your screen's import inside and it's good to go.

      _`const someComponent = lazy(() => import('./someComponent'))`_

  -   ### Try using well-defined PropTypes as much as possible

      Don't go putting PropTypes.any for your children components just because you didn't want to research what PropType is used for components. Unless you have a very specific need, try writing a well-defined PropType.


  -   ### Don't use your state variable as a dumping ground for your global variable

      Unless a variable is changing and that change requires a render, do not put it inside the state variable

      Do not do
      **this.state = {**
      **obj: { 'attr1':'val1', 'attr2': 'val2'}** 
      **}**

      Instead add it in _this_  itself
      **this.obj =  **{ 'attr1':'val1', 'attr2': 'val2'}****

  -   ### Don't use PureComponent everywhere

      If your component isn't re-rendering itself on the same prop or state, using PureComponent just adds a useless shallow checking of states and props. That's just unnecessary overhead.

  -   ### Don't have useless constructors

      For example - Do not use constructor just for super(props) when you don't touch props in there.

  -   ### Destructure your props

      Destructuring in itself is super helpful and destructuring your props lets others see exactly what props are you using for your component in a single place.

      So instead of  **const somefunc = (props) => { . . . }**
      Destructure them as  **const somefunc = ({ val1, val2, val3 }) =>  **{ . . . }****



  -   ### Use some form of state management if values are shared

      If the same values are required at multiple places, consider putting them in a global state that can be shared across the components. Not only will it reduce the number of times you declare and set that variable, but it'll also prevent the need for prop drilling.

      Find Redux too hard, too heavy, or too complex, go ahead and try other libraries. Redux is not always an absolute solution for all projects

  -   ### Make use of useReducer hook when you have multiple values that need to be updated together

      If you have a bunch of values that need to be updated at the same time, consider grouping them with a useReducer hook instead of having a separate state for each one of them. This will prevent unnecessary updates that would have happened if you had used useState for each one of them

  -   ### Convert your generic functionalities to a custom hook

      For example, If you need to store something in localstorage - make a custom hook for that.

      Now the code remains in one single location and is ready to be used anywhere you import that hook instead of being rewritten in each file that needs it.

  -   ### Use object for arguments instead of passing multiple arguments

      Imagine a scenario where you created a function that takes 3 parameters  _a, b, c_ - **someFunction (a, b, c)**

      Now, what if one of your peers decided to use that function but didn't need  _b?_ He'd have to pass  _null_ or  _undefined_  which seems kind of weird.

      Instead of going that way, try passing it as object attributes -  **someFunction ( {a, b, c} )**

      Now when you call that function, you can only specify the arguments that you need -  **someFunction ( {a:1, c:2} )**

      This will not only help you pass parameters optionally, but it'll also allow you to pass them in any order.
      Named Parameters at its best.

  -   ### Memoize your functional components to prevent useless re-renders

      You'd use PureComponent to prevent re-renders for class components, right? So why leave your functional components hanging?

      **React.memo**  is your functional component equivalent of PureComponent, give it a try.

      _`const MyComponent = React.memo(function MyComponent(props) { /* render using props */ });`_
