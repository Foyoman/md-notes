# js/ts

```js
// creates an array of unique values from the values of a single key across all objects in an object array
eventTypes() {
	return [...new Set(this.eventsUpcomingItems.map(event => event.eventType))]; // => ["Webinar", "CLE", "Networking"]
}
```

```js
// optional chaining for a method - this and parents exist and always return true in a Boolean(), the method showModal may not, thus ?.()
closeModal() {
	this.$parent.showModal?.(); // => undefined # if showModal doesn't exist, isn't accessible, or if it depends on it's parent
}
```

```js
// creates an array of unique values from the values of a single key across all objects in an object array within an object array
uniqLocations() {
	return [...new Set(this.partnerItems.map(item => item.locations).flat().map(item => item.state))]; // => ['NC', 'OR', 'OH', 'FL', 'NJ', 'IL', 'AZ', 'CA', 'CT', 'DC', 'GA', 'MA', 'MD', 'ME', 'NH', 'VA', 'VT', 'PA', 'NY']
}
```

```js
// sorts object array by date property
sortedPosts() {
	return this.posts.sort((a, b) => {
		const keyA = new Date(a.cardDate),
			keyB = new Date(b.cardDate)
		if (keyA > keyB) return -1;
		if (keyA < keyB) return 1;
		return 0;
	});
}
```

```js
Array.from(String(1234), Number); // => [1, 2, 3, 4]
```
