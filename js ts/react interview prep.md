- map and filter
- states
- props
- inline conditional statements (ternaries)
- event handling
- keys
- forms
- dynamic inputs
- css
- uncontrolled components (data from dom (useRef))
- virtual dom
- innerHTML
- react fragments
- REST api requests - network tab
- debouncing in react
- context api
- higher order components
- lazy loading in react - network tab (size/time)
- helper functions in react
- implementing recursion in react
- running arrays of functions (map)
- custom hooks in react
- promises and async/await
- code splitting in react (dynamic imports)
- creating a search filter in react
- adding typescript to react
- react testing library
- catching an api response
- pagination (slice)

## crud operations in api
- create, read, update, delete

## http request methods
- POST, GET, PUT, DELETE

---
# custom hook

```js
// ./hooks/useJSONPlaceholder
import { useState, useEffect } from "react";

function useData() {
	const [users, setUsers] = useState([]);
	const [posts, setPosts] = useState([]);
	
	const getUsers = () => {
		fetch("https://jsonplaceholder.typicode.com/users")
			.then((response) => response.json())
			.then((json) => setUsers(json));
	};
	
	const getPosts = () => {
		fetch("https://jsonplaceholder.typicode.com/posts")
			.then((response) => response.json())
			.then((json) => setPosts.json())
	};
	
	useEffect(() => {
		getUsers();
		getPosts();	
	}, []);
	
	return { users, posts };
}

export default useData;
```

```js
import useData from "./hooks/useJSONPlaceholder";

function App () {
	let {users, posts} = useData();
}
```

---
# fetch

## simple api call
```js
fetch("URL")
	// The fetch() method returns a Promise. After the fetch() method, include the Promise method then()
	// A Promise is an object representing the eventual completion or failure of an asynchronous operation
	// Call the fetch function passing the url of the API as a parameter
	.then(() => {
		// Your code for handling the data you get from the API
	})
	.catch(()=> {		 
		// This is where you run code if the server returns any errors
	});
```

## GET 
```js
// Get the Data from the URL
fetch("URL")
	// Transform the data into json
	.then((res) => res.json())
	.then((data) => {
		console.log(data);
	})
	.catch((error)=> {
		console.log(error);
	});
// In fetch API default is GET method.
```

## CREATE 
```js
fetch("URL",{
	// method changes
	method: 'POST',
	body: JSON.stringify({
		title: 'foo',
		body: 'bar',
		userId: 0
	}),
	headers: {
		"Content-type": "application/json; charset=UTF-8"
	}
})
	// Transform the data into json
	.then((res) => res.json())
	.then((data) => {
		console.log(data);
	})
	.catch((error)=> {
		console.log(error);
	});
```

## UPDATE 
```js
fetch("URL",{
	// method changes
	method: 'PUT',
	body: JSON.stringify({
		title: 'foo',
		body: 'bar',
		userId: 0
	}),
	headers: {
		"Content-type": "application/json; charset=UTF-8"
	}
})
	// Transform the data into json
	.then((res) => res.json())
	.then((data) => {
		console.log(data);
	})
	.catch((error)=> {
		console.log(error);
	});
```

## DELETE 
```js
fetch("URL", {
	method: 'DELETE'
} )
```

## fetch in react
```jsx
useEffect (() => {
	fetch ("https://jsonplaceholder.typicode.com/users")
		.then((response) => response.json())
		.then((json) => setUsers(json));
}, [])
```

---
# axios
`npm i axios`

```js
axios.get("URL")
	//handling the response_
	.then(() => {
		// the code for handling the data you get from api
	})
	.catch((error) => {
		// for handling the error thrown
		console_.log(error);
	});
```

## GET 
```js
axios.get("URL")
	.then(res => {
		console.log(res.data);
	});
// In axios API also default is GET method
```

## POST 
```js
const employee = {
	name: this.state.name,
	age: this.state.age,
	salary: this.state.salary,
}
// method .post
axios.post("URL", employee)
	.then(res => console.log(res.data));
```

## UPDATE
```js
const employee = {
	name: this.state.name,
	age: this.state.age,
	salary: this.state.salary,
}
// method .put
axios.put("URL", employee)
	.then (res => console.log(res.data));
```

## DELETE 
```js
// method .delete
axios.delete("URL")
	.then(res => console.log(res.data));
```

---
# async/await
using async/await, we can write code synchronously

the async keyword before a function has two effects:
- make it always return a promise
- allows awaiting to be used in it

the await keyword before a promise makes js wait until that promise settles, and then: 
- if it's an error, the exception is generated
- otherwise, it returns the result

## fetch
```js
// declare the async data fetching function
const fetchData = async () => {
	try {
		//get the data from the api
		const getData = await fetch("URL");
		// convert the data to json
		const json = await get_data.json();
	} 
	catch (error) {
		// make sure to catch any error
		console.log(error)
	}
}
// call the function
fetchData();
```

## axios
```js
const fetchData = asynce () => {
	try {
		const getData = await axios.get("URL");
		// remember in axios data is pre stored in json format
	}
	catch (error) {
		console.log(error)
	}
}
// call the function
fetchData();
```

---
# axios vs fetch

## fetch
- vanilla js
- can be read directly by browsers
- have to manually transform data
- more verbose
- harder to work with

## axios
- 3rd party library
- has to be compiled
- automatically transform data
- less verbose
- easier to work with

---
# form in react
```jsx
// form
const [form, setForm] = useState({
	name: "",
	email: "",
	babies: 0
});

async function onSubmit(e) {
	e.preventDefault();
	setSubscribed(true);

	const newSignup = {...form};

	await fetch("https://storkr-server.herokuapp.com/signups", {
		method: "POST",
		headers: {
			"Content-Type": "application/json",
		},
		body: JSON.stringify(newSignup),
	})
		.catch(error => {
			window.alert(error);
			return;
		});

	setForm({ name: "", email: "", babies: 0 });
}

function updateForm(value) {
	return setForm((prev) => {
		return { ...prev, ...value };
	});
}

<form onSubmit={ onSubmit } className='popout'>
	<label>
		Name
		<input 
			value={ form.name }
			onChange={(e) => updateForm({ firstName: e.target.value })}
			required 
			type="text" 
		/>
	</label>
	<label>
		Email
		<input 
			value={ form.email }
			onChange={(e) => updateForm({ email: e.target.value })}
			required 
			type="email" 
		/>
	</label>
	<label>
		No. of Babies
		<input 
			value={ form.babies }
			onChange={(e) => updateForm({ babies: e.target.value })}
			required 
			type="number" 
		/>
	</label>

	<Button type='submit' id='popout-button' className='subscribe d-flex btn-lg' style={{ opacity: '0.7,', fontWeight: 'bold' }}>Subscribe Now</Button>

</form>
```

---
# pagination

```jsx
import { useEffect, useState } from "react";

export default function App() {
	const [products, setProducts] = useState([]);
	const [page, setPage] = useState(1);
	const [totalPages, setTotalPages] = useState(0);
	
	const fetchProducts = async () => {
		const res = await fetch(`https://dummyjson.com/products?limit=10&skip=${page * 10 - 10}`);
		const data = await res.json();
		
		if (data && data.products) {
			setProducts(data.products);
			setTotalPages(data.total / 10);
		}
	};
	
	useEffect(() => {
		fetchProducts();
	}, [page]);
	
	const selectPageHandler = (selectedPage) => {
		if (
			selectedPage >= 1 &&
			selectedPage <= totalPages &&
			selectedPage !== page
		) {
			setPage(selectedPage);		
		}
	};
	
	return (
		<div>
		{ products.length > 0 && 
			<div>
			{/* products.slice(page * 10 - 10, page * 10) */}
			{ products.map((prod) => 
				<div>
					<img src={prod.thumbnail} alt={prod.title} key={prod.id} />
					<span>{prod.title}</span>
				</div>
			)}
			</div>
		}
		{ products.length > 0 &&
		<div>
			<span 
				onClick={() => selectPageHandler(page - 1)}
				className={page <= 1 ? "disabled" : ""}
			>
				⬅
			</span>
			{ [...Array(totalPages)].map(_, i) => 
			<span 
				className={page === i + 1 ? "selected" : ""}
				onClick={() => selectPageHandler(i + 1)} 
				key={i}>{i + 1}
			>	
				{i + 1}
			</span>
			}
			<span 
				onClick={() => selectPageHandler(page + 1)}
				className={page < totalPages ? "" : "disabled"}
			>
				➡
			</span>
		</div>
		}
		</div>
	)
}
```