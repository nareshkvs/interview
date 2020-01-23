ERROR SyntaxError: Unexpected token o in JSON at position 1

{  
   "data":{  
      "userList":[  
         {  
            "id":1,
            "name":"soni"
         }
      ]
   },
   "status":200,   
   "statusText":"OK"
}
JSON.parse(''above code);

Answer:
The JSON you posted looks fine, however in your code, it is most likely not a JSON string anymore, but already a JavaScript object. 
This means, no more parsing is necessary.

You can test this yourself, e.g. in Chrome's console:

new Object().toString()
// "[object Object]"

JSON.parse(new Object())
// Uncaught SyntaxError: Unexpected token o in JSON at position 1

JSON.parse("[object Object]")
// Uncaught SyntaxError: Unexpected token o in JSON at position 1
JSON.parse() converts the input into a string. The toString() method of JavaScript objects by default returns [object Object], resulting in the observed behavior.

Try the following instead:

var newData = userData.data.userList;
