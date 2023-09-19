# section 1: getting started

- a js superset
- a language building up on js
- adds new features + advantages to js
- ts can't be executed by js environments
- ts is a compiler which i run over my code to compile my ts to js
- the ts compiler compiels these new features to js workarounds
- compiles the nicer, easier ts into a more complex js snippet
- features are compiled to js "workarounds", possible errors are thrown
- it adds types
- catch errors
- unwanted behaviour at runtime
- mitigation strategies: add if check to add function, validate & sanitise user input - developers can still write invalid code! - ts is a "tool" that helps developers write better code!

```shell
npm install -g typescript
```

```shell
tsc using-ts.ts
```

```ts
const button = document.querySelector("button")!;
const input1 = document.getElementById("num1")! as HTMLInputElement;
const input2 = document.getElementById("num2")! as HTMLInputElement;

function add(num1: number, num2: number) {
	return num1 + num2;
}

button.addEventListener("click", function() {
	console.log(add(+input1.value, +input2.value));
});
```

ts adds: 
- types!
- next-gen js features (compiled down for older browsers)
- non-js features like interfaces or generics
- meta-programming features like decorators
- rich configuration options
- modern tooling that helps even in non-ts projects

## course outline 
- getting started
- ts basics
- compiler & configuration deep dive
- working with next-gen js code
- classes & interfaces
- advanced types & ts features
- generics
- decorators
- time to practice - full project
- working with namespaces & modules
- webpack & ts
- third-party libraries & ts
- react + ts & nodejs + ts

```shell
npm init
npm install --save-dev lite-server
npm start
```

`package.json`
```json
{
	...
	"scripts": {
		...
		"start": "lite-server"
	}
	...
}
```

---
# section 2: ts basics & basic types

## core types
- number - all numbers, no differentiation between integers or floats
- string - all text values
- boolean - true, false - just these two, no "truthy" or "falsy" values

```ts
function add(n1: number, n2: number, showResult: boolean, phrase: string) {
	// if (typeof n1 !== 'number' || typeof n2 !== 'number') {
	// throw new Error('Incorrect input!');
	// }
	const result = n1 + n2;
	if (showResult) {
		console.log(phrase + result);
	} else {
		return result;
	}
}

let number1: number;
number1 = 5;
const number2 = 2.8;
const printResult = true;
const resultPhrase = 'Result is: '

add(number1, number2, printResult, resultPhrase);
```

### type inference
- where you don't have specific type assignments
- ts will try its best to understand which type you have in a certain variable or constant
- `const number1 = 5` = `const number1: 5` because const

```ts
// redundant 
let number1: number = 5; // bad 
```

## object types
```ts
const person: {
	name: string;
	age: number;
}
```

## array types
```ts
// array of strings
let hobbies: string[];

for (const hobby of person.hobbies) {
	console.log(hobby.toUpperCase());
// console.log(hobby.map()); // !!! ERROR !!! GOOD !!!
}
```

## tuple types
```ts
// fixed type and length array
const role: [number, string] = [2, 'author']
```

## enums
```ts
// added by ts: automatically enumerated global constant identifiers
enum { NEW, OLD }
enum Role { ADMIN = 'ADMIN', READ_ONLY = 100, AUTHOR = 'AUTHOR' };

if (person.role === Role.ADMIN) {
	console.log("user is admin");
}
```

## any
`*`
- avoid when possible

## union types
```ts
function combine(input1: number | string, input2: number | string) {
	let result;
	if (typeof input1 === 'number' && typeof input2 === 'number') {
		result = input1 + input2;
	} else {
		result = input1.toString() + input2.toString();
	}
	return result;
}
```

## literal types
```ts
const number = 2.8;
```

## type aliases / custom types
```ts
type Combinable = number | string;
type ConversionDescriptor = 'as-number' | 'as-text';
```

## type alias & object types
```ts
type User = { name: string; age: number };
const u1: User = { name: 'Max', age: 30 };
```

## function return types & "void"
```ts
// void: function with no return statement
function printResult(num: number): void {
	console.log('Result: ' + num);
}

// undefined: return statement with no value
function printResult(num: number): undefined {
	console.log('Result: ' + num);
	return;
}

printResult(add(5, 12));
```

## functions as types
```ts
let combineValues: (a: number, b: number) => number;
```

## function types & callbacks
```ts
function addAndHandle(n1: number, n2: number, cb: (num: number) => void) {
	const result = n1 + n2;
	cb(result);
}
```

## unknown type
```ts
let userInput: unknown;
let userName: string;

userInput = 5;
userInput = 'Max';
if (typeof userInput === 'string') {
	userName = userInput;
}
```

## never type
```ts
// never returns anything
function generateError(message: string, code: number): never {
	throw { message: message, errorCode: code };
}
```

---
# section 3: the ts compiler (and its configuration)

## watch mode
```sh
# watch one specific file to compile after every change
tsc app.ts --watch

# watch the whole project
tsc --init # => tsconfig.json
tsc # compile all files in project
tsc -w watch all files
```

- including/excluding files

## setting a compilation target
```json
{
	"compilerOptions": {
		"target": "es6",
	}
}
```

## understanding ts core libs
```json
{
	"compilerOptions": {
		// defaults
		"lib": [
			"dom",
			"es6",
			"dom.iterable",
			"scripthost",
		],
	}
}
```

## more configuration & compilation options
```json
{
	"compilerOptions": {
		// "allowJs": true,
		// "checkJs": true,
		// "jsx": "preserve",
		// "declaration": true,
		// "declarationMap": true,
	}
}
```

## working with source maps
```json
{
	"compilerOptions": {
		// "sourceMap": true,
	}
}
```

- browser sources tab in dev tools
- .js.map files

## rootDir and outDir
```json
{
	"compilerOptions": {
		"outDir": "./dist",
		"rootDir": "./src",
		"removeComments": true,
		// "noEmit": true,
		// "importHelpers": true
		// "downlevelIteration": true,
	}
}
```

- src: ts files
- dist: js filesst

## stop emitting files on compilation errors
```json
{
	"compilerOptions": {
		"noEmitOnError": true,
	}
}
```

## strict compilation
```json
{
	"compilerOptions": {
		"strict": true,
		// "noImplicitAny": true, /* Enable error reporting for expressions and declarations with an implied 'any' type. */
		// "strictNullChecks": true, /* When type checking, take into account 'null' and 'undefined'. */
		// "strictFunctionTypes": true, /* When assigning functions, check to ensure parameters and the return values are subtype-compatible. */
		// "strictBindCallApply": true, /* Check that the arguments for 'bind', 'call', and 'apply' methods match the original function. */
		// "strictPropertyInitialization": true, /* Check for class properties that are declared but not set in the constructor. */
		// "noImplicitThis": true, /* Enable error reporting when 'this' is given the type 'any'. */
		// "useUnknownInCatchVariables": true, /* Default catch clause variables as 'unknown' instead of 'any'. */
		// "alwaysStrict": true, /* Ensure 'use strict' is always emitted. */
	}
}
```

## code quality options
```json
{
	"compilerOptions": {
		/* Additional Checks */
		"noUnusedLocals": true, /* Enable error reporting when local variables aren't read. */
		"noUnusedParameters": true, /* Raise an error when a function parameter isn't read. */
		"noImplicitReturns": true, /* Enable error reporting for codepaths that do not explicitly return in a function. */
	}
}
```

## debugging with vscode
```ts
{
	"compilerOptions": {
		"sourceMap": true,
	}
}
```

- place breakpoints
- launch/start debugging
- point it at localhost:3000
- compile

---
# section 4: next-generation js & ts (es6)
- `var` (old)
	- global and function scope
- `let`, `const`
	- block scope - only available in the block you define it in, or lower. forces you to write cleaner code
- arrow function
	- implicit return (one expression)
	- omitting parentheses with single parameter
- default function parameters
	- variable parameters first, parameters with default values last
- the spread operator
	- arrays are objects, and objects are reference values. when we push we change the memory but not the address
- rest parameters
	- accept an unlimited amount of arguments
- array & object destructuring

```ts
// block scope
if (age3 > 20) {
	let isOld = true;
}
```

```ts
// arrow functions
const add = (a: number, b: number) => a + b;
const printOutput: (a: number | string) => void = output => console.log(output);
if (button2) {
	button2.addEventListener('click', event => console.log(event));
}
```

```ts
// default function parameters
const add = (a: number, b: number = 5) => a + b;
```

```ts
// spread operator
const hobbies = ['Sports', 'Cooking'];
const activeHobbies = ['Hiking']

activeHobbies.push(...hobbies)

const person = {
	name: 'Max',
	age: 30,
};

const copiedPerson = { ...person };
```

```ts
// rest parameters
const add = (...numbers: number[]) => {
	return numbers.reduce((curResult, curValue) => {
		return curResult + curValue;
	}, 0);
};

const addedNumbers = add(5, 10, 2, 3.7);

// with tuple
const add = (...numbers: [number, number, number]) => {
	return numbers.reduce((curResult, curValue) => {
		return curResult + curValue;
	}, 0);
};

const addedTuple = add(5, 10, 2);
```

```ts
// array & object destructuring
const [hobby1, hobby2, ...remainingHobbies] = hobbies;

const { name: userName, age } = person2;
// alias - rename
console.log(username, age)
```

---
# section 5: classes & interfaces
- object-oriented programming (oop)
	- work with real-life entities in your code
		- `ProductList: {}`
			- renders a list of products which were fetched from a server (database)
			- object holds rendering + fetching logic
		- `Product`
			- renders details about a product and allows addition to cart
			- object holds rendering + cart-adding logic
		- `ShoppingCart`
			- renders cart products and total and allows user to order them
			- object holds rendering + ordering (server communication) logic
	- objects
		- "the things you work with in code"
		- instances of classes (= based on classes)
		- class-based creation is an alternative to using object literals!
	- classes 
		- "blueprints for objects" (theoretical definition)
		- define how objects look like, which properties and methods they have
		- classes make creation of multiple, similar objects much easier
- compiling to js
- constructor functions & the "this" keyword
- "private" and "public" access modifiers
	- public properties
		- accessible outside of the class
	- private modifier
		- properties only accessible by methods within the class
- shorthand initialisation
	- `constructor(protected readonly id: string, public name: string) {}`
- "readonly" properties
	- can't be changed after initialisation
- inheritance
	- `super`: whenever I add my own constructor that has a constructor in a class that inherits from another class
- overriding properties & the "protected" modifier
	- private properties are only accessible from within the class that they're defined, not classes that inherit from that class
	- `protected`: is like `private`, but allows property to be available in classes that extend from the class
- getters & setters
	- `get` and `set`
- static methods & properties
	- `static`: so I don't have to instantiate just to call a utility method
		- inaccessible from within the class from non-static parts
		- not available on instance 
		- the idea is that they're detached from instances
		- `Department.fiscalYear`: gives access to static properties from inside the class
	- `this`: refers to the instance created based on the class
- abstract classes
	- whenever I want to ensure a certain method is available in all classes based on some base class, and when I know that the exact implementation will depend on the specific version
	- when I can't provide a general method but when I want to enforce that this method exists but the inheritance class will need to provide it's own implementation because I can't provide a default implementation in the base class
	- useful for when I want to ensure that all classes based on a base class share some common method or property but when I want to make sure I don't have to provide the concrete value/implementation in the base class but the inheritance class
	- abstract classes can't be instantiated themselves
- singletons & private constructors
	- singleton - ensure I have only one instance of a certain class
	- `private static instance: AccountingDepartment`
		- `static` property, accessible from the class itself, `private`: but only from inside the class, `instance: AccountingDepartment`: and the value that we store in there will be of type `AccountingDepartment`

```ts
class Department {
	name: string;
	
	constructor(n: string) {
		this.name = n;
	}
	
	describe(this: Department) {
		console.log('Department: ' + this.name);
	}
}

const accounting = new Department('Accounting');

accounting.describe();

const accountingCopy = { name: 'DUMMY', describe: accounting.describe };

accountingCopy.describe();
```

## interfaces
- clear: only for objects
- implement an interface in a class
	- can be used as a contract a class can implement and has to adhere to
	- classes can `implement` multiple interfaces
- a bit like abstract classes but no implementation details
- `readonly`: set only once and cannot be changed after the object has been initialised 
- can inherit from multiple: `extends`
- optional properties
	- `outputName?: string`
	- these 3 are loosely related: optional property in the interface, optional property in the class, then the optional parameter in the constructor
- optional parameters & properties
	- again, optional property in the interface, in the class, and optional parameter in the constructor
	- optional parameter in constructor: default value or question mark
- compiling interfaces to js 
	- interfaces are not compiled to js
- interfaces - pure ts feature

---
# section 6 - advanced types
- intersection types
- more on type guards
- discriminated unions
- type casting
- index properties 
- function overloads
- optional chaining
- nullish coalescing

## intersection types
```ts
type ElevatedEmployee = Admin & Employee;
type Universal = Combinable & Numeric;
```

## type guards
```ts
if ('privileges' in emp) {
	// emp.privileges
}

// class Truck; type Vehicle = Car | Truck;
if (vehicle instanceof Truck) {
	// ...
}

// use `in` with types, and `instanceof` with classes

// discriminated union
interface Bird {
	type: 'bird';
	flyingSpeed: number;
}

interface Horse {
	type: 'horse';
	runningSpeed: number;
}

type Animal = Bird | Horse;

function moveAnimal(animal: Animal) {
	let speed;
	switch (animal.type) {
		case 'bird':
			speed = animal.flyingSpeed;
			break;
		case 'horse':
			speed = animal.runningSpeed;
	}
	console.log('Moving at speed: ' + speed);
}

moveAnimal({type: 'bird', flyingSpeed: 10});
```

## type casting
```ts
// const userInputElement = <HTMLInputElement>document.getElementById('user-input')!;
const userInputElement = document.getElementById('user-input');

if (userInputElement) {
	(userInputElement as HTMLInputElement).value = 'Hi there!'
}
```

## index types
```ts
interface ErrorContainer {
	[prop: string]: string;
}

const errorBag: ErrorContainer = {
	email: 'Not a valid email!',
	username: 'Must start with a capital character!'
}
```

## function overloads
```ts
function add(a: number, b: number): number
function add(a: string, b: string): string;
function add(a: string, b: number): string;
function add(b: number, b: string): string;
function add(a: Combinable, b: Combinable) {
	// ...
}

const result = add('Max', ' Schwarz');
result.split(' ');
```

## optional chaining
```ts
console.log(fetchedUserData?.job?.title);
```

## nullish coalescing
```ts
const userInput = '';

const storedData = userInput ?? 'DEFAULT'; // only falls back on `null` or `undefined`

console.log(storedData) // => ''
```

---
# generics
```ts
const names: Array<string> = ['Max', 'Manuel']; // string[]
const Promise<number> = new Promise((resolve, reject) => {
	// ...
})
```

## constraints
```ts
function merge<T extends object, U extends object>(objA: T, objB: U) {
	// ...
}

interface Lengthy {
	length: number;
}

function countAndDescribe<T extends Lengthy>(element: T): [T, string] {
	// ...
}

// keyof
function extractAndConvert<T extends object, U extends keyof T>(obj: T, key: U) {
	// ...
}
```

- reference type: basically, `{name: 'Max'} !== {name: 'Max'}`

## utility
```ts
let courseGoal: Partial<CourseGoal> = {};
const names: Readonly<string[]> = ['Max', 'Anna'];
```

- unions: flexibility to call a function with either type
- generics: lock in that type throughout the class/function

---
# decorators
```ts
// wild shit
```
