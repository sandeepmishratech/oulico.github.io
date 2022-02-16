---

layout: post
title: "This keyword in Javascript"
date: 2022-02-15 08:25:50 +0900
categories: Notes-JavaScript
tags: Notes JavaScript This
---





This key word variable: Special variable that is created for every execution context (every function).

It is one of the three components of any execution context (Variable environment, Scope chain, `this` keyword)

It points to the owner of that function.

The value of `this` is **not static**. So It's not always the same. It **depends on how the function is called** and its **value is only assigned when the function is actually called**.



## 4 different ways in which function can be called

1. Method (function attached to the object)

   - this =  Object that is calling the method

   When we call a method, the this keyword inside that method will simply point to the **object** on which the method is called. In other words, it point to the object that is calling the method.

   ```js
   const oulico = {
     name: 'oulico',
     year: 1990,
     calcAge: function() {
       return 2037 - this.year;
     }
   };
   oulico.calcAge();
   
   ```

2. Simple function call 

   - this = undefined

     Simply calling them as normal functions, `this` will simply be `undefined`. 

     However it is only valid for `strict mode`. If you're not in `strict mode`, `this` will actually point to the `global object`, which in case of the browser is the window object. So use always `strict mode`

3. Arrow functions

   - this = this of surrounding function (`lexical this`)

     `Arrow functions` do not get their own `this` keyword. Instead, if you use `the this variable` in an arrow function, it will simply be the **this keyword of the surrounding function**. (of the parent function)

     This is called the `lexical this key word`. Because it gets picked up from the out lexical scope of the arrow function.

     Never forget this because one day you'll run into a bug because of this behavior. **Arrow functions don't get their own `this keyword`**

     

4. Event listener 

   - This = DOM element that the handler is attached to 

 ⚠︎`This` does **NOT** point to the function itself, and also **Not** the its variable environment



Other ways in which we can call al function : `new`, `call`, `apply`, `bind`







## This keyword in practice



#### 1. Out side of a function 

```js
'use strict';
console.log(this);
```

Result: 

![image-20220215144956876](/assets/img/2022-02-08-This-keyword-in-Javascript/image-20220215144956876.png)



- The global `this`



#### 2. Inside of a regular function

```js
'use strict';
const calcAge = function (birthYear) {
  console.log(2037 - birthYear);
  console.log(this);
};
calcAge(1991);

```

Result: 

![image-20220215145331221](/assets/img/2022-02-08-This-keyword-in-Javascript/image-20220215145331221.png)



Why?

- It is a call of `this` function without the function being attached to any object.

- It's in `strict mode`.
- In a regular function call, `this` keyword simply point to `undefined`.



#### 3. In an arrow function

```js
'use strict';
const calcAgeArrow = birthYear => {
  console.log(2037 - birthYear);
  console.log(this);
};
calcAgeArrow(1980);
```

Result:

![image-20220215152808533](/assets/img/2022-02-08-This-keyword-in-Javascript/image-20220215152808533.png)



Why?

- It is the `this` keyword of the parent's scope.
- In arrow function, `this` keyword is `lexical this`



#### 4. Inside of a method

```js
'use strict';
const oulico = {
  year: 1991,
  calcAge: function() {
    console.log(this);
  }
}
jonas.calcAge();

```

Result: 

![image-20220215154045490](/assets/img/2022-02-08-This-keyword-in-Javascript/image-20220215154045490.png)



Why?

- `oulico` here is the **owner of the method**.

- So inside of the `calcAge`, the `this` is `oulico`

  

We can use that data to calculate the age:

```js
'use strict';
const oulico = {
  year: 1991,
  calcAge: function () {
    console.log(2037 - this.year);
  },
};
oulico.calcAge();
```

Result:

![image-20220215154536341](/assets/img/2022-02-08-This-keyword-in-Javascript/image-20220215154536341.png)





---







## ⚠︎ Important

 `this` keyword will point to the object that is calling the method.

That means, that the `this` keyword will not simply point at the object in which we wrote the method.



```js
'use strict';
const oulico = {
  year: 1991,
  calcAge: function () {
    console.log(2037 - this.year);
  },
};
oulico.calcAge();

const matilda = {
  year: 2017,
};

matilda.calcAge = oulico.calcAge;// method borrowing
matilda.calcAge();//it is matilda which is calling the method.
```



Even though the `this` keyword's written in `oulico`, still it points to Matilda which calls the method.



