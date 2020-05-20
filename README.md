# ES6 Javascript
Recently, I completed ES6 Javascript tutorial on Udemy by Stephen Grider: https://www.udemy.com/course/javascript-es6-tutorial/. While I have been using Javascript for a long time, I had not used many of these new features. Hence thought of capturing key concepts on a page for easy reference. Thanks for the wonderful course, Stephen. 

The following concepts are covered:
* General Points
* `forEach`
* `map`
* `filter` + fat arrow `=>` function declaration. 
* `find`
* `every` & `some`
* `reduce`
* Rest and Spread operators

## General Points
* Use `const` to define constants and `let` to define variables instead of the `var` keyword to define variables. 
* Use template strings to mix text and variable data to output messages. For example \``Your number doubled is ${2 * number}`\` - Here `number` is a variable and also note that the template string has to be enclosed with backticks (\`).
* __Enhanced Object Literals__: 
  * If JSON key value pair both have same name (value is variable name), you can shorten how to write it. E.g. `{color: color}` can be written as `{color}`. Note that internal representation does not change. So if color has value blue, the preceding code will translate to `{'color': 'blue'}` 
  * If an object defines a function in a key value pair as `makeSomething: function() {}`, it can be re-written in a simpler way as `makeSomething() {}`.
* __Default Function Arguments__: Function declaration can define default values of input variables to be used if the invocation does not provide the value. E.g. function doSomething(x = 10, y = 20) will use 10 and 20 as default values of x and y respectively if the invocation does not provide the input values.  

## `forEach`
Instead of using a `for` loop, use `forEach` to iterate through an array. 
~~~~
var employees = [
  {id:1, name:'Ram'},
  {id:2, name:'Rahim'}
];

employees.forEach(function(employee) {
  print(employee);
});
~~~~

## `map`
The `map` helper can be used to 'map' source array elements to corresponding target array elements. For example, the code below extracts just the names from the employee objects. 
~~~~
var employees = [
  {id:1, name:'Ram'},
  {id:2, name:'Rahim'}
];

var employeeNames = employees.map(function(employee) {
  return (employee.name);
});
~~~~

## `filter`
The `filter` helper can be used to 'filter' the input array elements matching the filter criteria into the output array. For example, the code below filters only the female employees. 

Also, note that the fat arrow format of the function definition is shown below. So, instead of using `function(employee)` declaration, the equivalent `(employee) =>` declaration is used. 
~~~~
var employees = [
  {id:1, name:'Ram', gender: 'male'},
  {id:2, name:'Rahim', gender: 'male'}, 
  {id:3, name:'Girija', gender: 'female'}
];

var femaleEmployees = employees.filter((employee) => {
  return (employee.gender === 'female');
});
~~~~

## `find`
The `find` helper works similar to `filter` but returns the first item matching the find criteria. For example, the code below finds an employee named Rahim. 
~~~~
var employees = [
  {id:1, name:'Ram', gender: 'male'},
  {id:2, name:'Rahim', gender: 'male'}, 
  {id:3, name:'Girija', gender: 'female'}
];

var rahim = employees.find((employee) => {
  return (employee.name === 'Rahim');
});
~~~~

## `every` & `some`
The `every` helper checks if all the items in an array satisfy some condition and outputs a single boolean value. It performs a logical and (`&`) to a conditional applied to each input array item to output the boolean result. For example, the code below checks if all the employees are male and returns `False`.
~~~~
var employees = [
  {id:1, name:'Ram', gender: 'male'},
  {id:2, name:'Rahim', gender: 'male'}, 
  {id:3, name:'Girija', gender: 'female'}
];

var allMale = employees.every((employee) => {
  return (employee.gender === 'male');
});
~~~~

The `some` helper checks if at least one of the items in an array satisfies some condition and outputs a single boolean value. It performs a logical or (`|`) to a conditional applied to each input array item to output the boolean result. For example, the code below checks if at least one employee is male and returns `True`.
~~~~
var employees = [
  {id:1, name:'Ram', gender: 'male'},
  {id:2, name:'Rahim', gender: 'male'}, 
  {id:3, name:'Girija', gender: 'female'}
];

var atLeastOneMale = employees.some((employee) => {
  return (employee.gender === 'male');
});
~~~~

## `reduce`
The `reduce` helper 'reduces' the input array into a single output value which could be a number, object, or anything else. For example, the code below tabulates the number of male and female employees into an output JSON object of the format `{male: #, female: #}`. 

Note the following two points:
* The `reduce` function takes two parameters: 
  * the function (like the rest of the helpers), and 
  * the initial value of the accumulator - for example `{male: 0, female: 0}` in the code below. 
* The function itself has two parameters:
  * the name of the accumulator variable - for example `acc` in the code below, and 
  * the item of the array (like the rest of the helpers).

The code below returns `{"male":2,"female":1}`.
~~~~
var employees = [
  {id:1, name:'Ram', gender: 'male'},
  {id:2, name:'Rahim', gender: 'male'}, 
  {id:3, name:'Girija', gender: 'female'}
];

var genderCounts = employees.reduce((acc, employee) => {
    if (employee.gender === 'male') return {male: ++acc.male, female: acc.female}
    if (employee.gender === 'female') return {male: acc.male, female: ++acc.female}
}, {male: 0, female: 0});
~~~~

## Rest & Spread Operators
The `reduce` helper 'reduces' the input array into a single output value which could be a number, object, or anything else. For example, the code below tabulates the number of male and female employees into an output JSON object of the format `{male: #, female: #}`. 
