# Function.prototype.call() VS Function.prototype.apply() VS Function.prototype.bind()

> call method which is used to invoke a function directly by passing in the reference, which points to the this variable inside the method.

> apply method is same as call method, but it takes second arguement as arraylist of the parameter which needs to be passed to the function

> bind method doesnot directly invokes the method. it gives you the copy of that exactly same method which can be invoke later

    let name = {
      firstname: "naresh", 
      lastname: "kumar", 
      printFullName: function() {
              console.log(this.firstname+ " "+this.lastname);
        } 
    }
    
    console.log(Object.keys(name).length); // Object Length
    name.printFullName();

    let name2 = { 
		firstname: "rudransh", 
		lastname: "Narayan"
	};

> Function borrowing

	name.printFullName.call(name2);
  
  In general case, we dont keep our methods inside the object if you want to re-use them rather we can create as a seperate function like 

    let name = {
      firstname: "naresh", 
      lastname: "kumar"
    }

    let name2 = { 
      firstname: "rudransh", 
      lastname: "Narayan"
    };

    let printFullName = function() {
      console.log(this.firstname+ " "+this.lastname);
    }	

    printFullName.call(name);
    printFullName.call(name2);
    
 What if we had more parameters in to the defined function  like
 
    let printFullName = function(hometown, state) {
      console.log(this.firstname+ " "+this.lastname+" from "+hometown+" , "+state);
    }
    
We can call above function like 

    printFullName.call(name, "Hyderabad", "Telangana");
    printFullName.call(name, "Vizag", "AP");
    
 the first parameter always be the reference to this variable, and the later arguments can be arguemtns to the function.
 
 ###### Only diff between apply and call method is the way we pass the arguemtns 

    printFullName.apply(name, ["Hyderabad", "Telangana"]);  // pass the arguements as arraylist
    printFullName.apply(name, ["Vizag", "AP"]);
    
###### bind method is same as call method but the difference is instead of calling to the function directly, it binds and keep a copy of the method and use/invoke it later

    let printMyName = printFullName.bind(name, "Hyd", "AP");
    console.log(printMyName); // copy of function like ƒ (hometown, state) {
                              //  console.log(this.firstname+ " "+this.lastname+" "+ hometown+","+ state);
                              //          }
    printMyName();     //naresh kumar Hyd,AP
    
    
