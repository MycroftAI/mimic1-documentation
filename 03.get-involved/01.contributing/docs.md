---
title: 'How to Contribute'
taxonomy:
    category:
        - docs
---

For those who wish to help contribute to the development of mimic there are a few things to keep in mind. 
  
#### Git branching structure
We will be using a branching struture similar to the one described in [this article](http://nvie.com/posts/a-successful-git-branching-model/)
  
##### In short

- `master` branch is for stable releases, 
  
- `development` branch is where development work is done between releases,
  
- Any feature branch should branch off from `development`, and when complete will be merged back into `development`.
  
- Once enough features are added or a new release is complete those changes in `development` will be merged into `master`, 
  then work can continue on `development` for the next release. 


#### Coding Style Requirements
To keep the code in mimic coherent a simple coding style/guide is used. It should be noted that the current codebase as a whole does not meet some of these guidlines,this is a result of coming from the flite codebase. As different parts of the codebase are touched, it is the hope that these inconsistancies will diminish as time goes on.

- **Indentation**

  Each level of indentation is *4 spaces*.

- **Braces**

  Braces always comes on the line following the statement.

  **_Example_**

  ```c
  void cool_function(void)
  {
      int cool;
      for (cool = 0; cool < COOL_LIMIT; cool++)
      {
          [...]
          if (cool == AWESOME)
          {
              [...]
          }
      }
  }
  ```

- **If-statements**

  Always use curly braces.
  
  **_Example_**

  ```c
  if(condition)
  {                             /*always use curly braces even if the 'if' only has one statement*/
      DoJustThisOneThing();        
  }
  
  if(argv[i][2] == 'h' &&      /*split 'if' conditions to multiple lines if the conditions are long */
     argv[i][3] == 'e' &&      /*or if it makes things more readable. */
     argv[i][4] == 'l' && 
     argv[i][5] == 'p')
  {
        /*example taken from args parsing code*/
        /* code */
  }
  else if(condition)
  {
        /* code */
  }
  else
  {
      /* code */
  }
  ```
  
- **Switch-statements**

  Always keep the break statement last in the case, after any code blocks.

  **_Example_**

  ```c
  switch(state)
  {
      case 1:
      {               /* even if the case only has one line, use curly braces (similar reasoning as with if's) */ 
          doA(1);
      } break;
                          /* separate cases with a line */
      case 2:             /* unless it falls into the next one */
      case 3:
      {
          DoThisFirst();
      }                   /* no break, this one also falls through */
      case 4:
      {                   /* notice that curly braces line up with 'case' on line above */
          int b = 2;
          doA(b);
      } break;        /* putting 'break' on this line saves some room and makes it look a little nicer */
  
      case 5:
      {
          /* more code */
      } break;
  
      default:        /* It is nice to always have a default case, even if it does nothing */
      {
          InvalidDefaultCase(); /* or whatever, it depends on what you are trying to do. */
      }
  }
  ```


- **Line length**

  There's no hard limit but if possible keep lines shorter than *80 characters*.
