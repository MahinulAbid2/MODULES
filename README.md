# Higher Order function
> Target: remix
* This function is mainly focused on handling `errors` in `remix-react`.
* Using `higher order function`, I can <b>centralize</b> error handling. 

```javascript
const catchAsync = (fn) => {
  return fn().catch((err) => { throw err; });
};

class Test {
  getData(a, b) {
    return catchAsync(async () => { // Return catchAsync to handle errors
      /**
       *  I can access a, b here.
       *  Do something with a, b in the argument
       */
      console.log(a, b);
      return a;
    });
  }
}

const x = new Test(); 
const z = x.getData(20, 10);
console.log(z) // output: 20, cz I returned a.


/**
 * If you want to log the result, 
 * use `then` or async/await since `getData` returns a promise
*/
z.then(result => console.log('Result:', result))
.catch(err => console.error('Error:', err));


```

