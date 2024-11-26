# ActForCommunity
Website for non-profit organization

Hey guys, I'm glad to work with you guys. Let me introduce some simple rules of collaborative development.

## 1. document syntax
Documents should be written in [markdown](https://www.markdownguide.org/basic-syntax/).

## 2. git rules
We are a small project, so I decide not to use gitflow standard. But I still suggest use different branches so we can have a better management, it's not mandatory. **STATE CLEARLY WHAT YOU DID IN COMMIT**. This is important and mandatory, never leave a blank of commit. I'll review each PR before merging.

## 3. code conventions
1. I hope we can unify the format of naming into camel-case(even though the repo name is in pascal).
2. ### Clear variable name

   _Bad 👎🏻_

   ```javascript
   let a = 42;
   ```

   _Good 👍🏻_

   ```javascript
   let age = 42;
   ```
3. ### unify naming format
   _Bad 👎🏻_

   ```javascript
   let wWidth = 640;
   let w_height = 480;
   ```

   _Good 👍🏻_

   ```javascript
   let windowWidth = 640;
   let windowHeight = 480;
   ```
4. ### comments
   _Bad 👎🏻_

   ```javascript
   const cdr = 700;
   ```

   _Good 👍🏻_

   More often comments should contain some 'why' and not some 'what'. If the 'what' is not clear in the code, the code is probably too messy.
   ```javascript
    // The number of 700ms has been calculated empirically based on UX A/B test results.
    // @see: <link to experiment or to related JIRA task or to something that explains number 700 in details>
    const callbackDebounceRate = 700;
   ```
   Also use only English in comments.
5. ### exception handling
   Don't just ignore errors.

   _Bad 👎🏻_

   ```javascript
   try {
     // code
   } catch (error) {
     // tss... 🤫
   }
   ```

   _Good 👍🏻_

   ```javascript
   try {
     // code
   } catch (error) {
     setErrorMessage(error.message);
     // and/or
     logError(error);
   }
    ```
6. ### nest
	_Bad 👎🏻_
	
	```javascript
	function someFunction() {
	  if (condition1) {
	    if (condition2) {
	      asyncFunction(params, (result) => {
	        if (result) {
	          for (;;) {
	            if (condition3) {
	            }
	          }
	        }
	      })
	    }
	  }
	}
	```
	
	_Good 👍🏻_
	
	```javascript
	async function someFunction() {
	  if (!condition1 || !condition2) {
	    return;
	  }
	  
	  const result = await asyncFunction(params);
	  if (!result) {
	    return;
	  }
	  
	  for (;;) {
	    if (condition3) {
	    }
	  }
	}
	```
7. ### testing
	test before commit
8. ### function
	Divide code into functions