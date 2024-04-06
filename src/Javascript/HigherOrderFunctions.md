# Higher Order Functions 
> Function that takes one or more functions as arguments and returns a function or both, i.e: map and reduce 

> Map takes in an array of values and applies a transformation to each of the values in the array.

```JS
const devs = [
  {firstName: 'Nicole', lastName: 'Lam', specialty: 'Accessibility}, 
  {firstName: 'Jen', lastName: 'Dmytrenko', specialty: 'Tailwind'}
]

const result = devss.map(dev => dev.firstName + ' ' + dev.lastName);
console.log(result); //['Nicole Lam', 'Jen Dmytrenko']

const specialty = devs.map(dev => dev.specialty);
console.log(specialty); //['Accessibility, 'Tailwind']\

//Callback function that will be passed as a parameter in the higher order function 
const callbackFunction1 = () => {
  console.log('I am a callback function 1');
}

const callbackFunction2 = () => {
  console.log('I am a callback function 2');
}

//higher order function 
const higherOrderFunction = (callbackFunction) => {
  console.log('I am a higher function')
  callbackFunction()
}

higherOrderFunction(callbackFunction1)
higherOrderFunction(callbackFunction2)
```

> in the above code, higherOrderFunction() is a higher order function because we are passing a callback function as a parameter to it!
> higherOrderFunction is invoked with callbackFunction as its argument.
> inside higherOrderFunction, it logs 'I am a higher function' to the console.
> it calls the function passed to it (callbackFunction), which logs 'I am a callback function' to the console.

# Benefits of Higher Order Functions  
- ✅ improve legibility of code, making it more concise and easy to undersetand 
- ✅ can speed up developemnt process 
- ✅ make it easier to debug code