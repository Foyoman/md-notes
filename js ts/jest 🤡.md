## test flow
1. import the function to test
2. give an input to the function
3. define what to expect as the output
4. check if the function produces the expected output
input - expected output - assert the result

```sh
mkdir getting-started-with-jest && cd $_
npm init -y
npm i jest --save-dev
```

```json
"scripts": {
	"test": "jest"
},
```

```js
const filterByTerm = require("../src/filterByTerm");
describe("Filter function", () => {
	const input = [
		{ id: 1, url: "https://www.url1.dev" },
		{ id: 2, url: "https://www.url2.dev" },
		{ id: 3, url: "https://www.link3.dev" },
	];
	
	test("it should filter by a search term (link)", () => {
		const output = [{ id: 3, url: "https://www.link3.dev" }];
		
		expect(filterByTerm(input, "link")).toEqual(output);
		// how I would call the function in my code:
		// filterByTerm(inputArr, "link");
		
		expect(filterByTerm(input, "LINK")).toEqual(output); // New test
	});
	
	test("it should filter by a search term (uRl)", () => {
		const output = [
			{ id: 1, url: "https://www.url1.dev" },
			{ id: 2, url: "https://www.url2.dev" },
		];
		
		expect(filterByTerm(input, "uRl")).toEqual(output);
	});
	
	test("it should throw when searchTerm is empty string", () => {
		expect(() => {
			filterByTerm(input, "");
		}).toThrow("searchTerm cannot be empty");
	});
});
```

code coverage:
1. via the command line by passing the flag `--coverage`
2. by configuring Jest in `package.json`

```sh
npm test -- --coverage
```

```json
"scripts": {
	"test": "jest --coverage"
},
// ||
"scripts": {
	"test": "jest"
},
"jest": {
	"collectCoverage": true,
	"coverageReporters": ["html"]
},
```

```sh
nvm install node
```

```json
"scripts": {
	"test": "node --experimental-vm-modules node_modules/jest/bin/test.js"
},
"type": "module",
```

```js
export function simpleFunc() {
	return "hello!";
}

export function complexFunc() {
	return "complex!";
}
```

```js
import { simpleFunc } from "../src/SimpleModule";

describe("A simple module", () => {
  test("it should say hello", () => {
    expect(simpleFunc()).toEqual("hello!");
  });
});
```