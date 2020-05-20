Recently, I completed ES6 Javascript tutorial on Udemy by Stephen Grider: https://www.udemy.com/course/javascript-es6-tutorial/. While I have been using Javascript for a long time, I had not used many of these new features. Hence thought of capturing key concepts on a page for easy reference. Thanks for the wonderful course, Stephen. 

The following concepts are covered:
* `forEach`
* `map`
* `filter`

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
The `filter` helper can be used to 'filter' the input array elements matching the filter criteria into the output array. For example, the code below filters only the female employees. Also, note that the fat arrow format of the function definition is shown below. So, instead of using `function(employee)` declaration, the equivalent `(employee) =>` declaration is used. 
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
