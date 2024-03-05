```ts
const dateAndTimes = sortedData.map((flight) =>
	dir === "arr" ? flight.arr_time : flight.dep_time
);

	const dates = dateAndTimes.map((dateAndTime) => {
	const dateObject = new Date(dateAndTime);
	const year = dateObject.getFullYear();
	const month = String(dateObject.getMonth() + 1).padStart(2, "0"); // Month is zero-based
	const day = String(dateObject.getDate()).padStart(2, "0");
	
	return `${year}-${month}-${day}`;
});

const dateSet = [...new Set(dates)]
console.log(dateSet);
```