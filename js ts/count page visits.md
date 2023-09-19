```tsx
// count page visits
useEffect(() => {
	const countKey = process.env.REACT_APP_COUNT_KEY as string;
	
	const getOrdinal = (n: number) => {
		let ord: 'th' | 'st' | 'nd' | 'rd' = 'th';
		
		if (n % 10 === 1 && n % 100 !== 11) {
			ord = 'st';
		} else if (n % 10 === 2 && n % 100 !== 12) {
			ord = 'nd';
		} else if (n % 10 === 3 && n % 100 !== 13) {
			ord = 'rd';
		}
		
		return String(n) + ord;
	}
	
	if (localStorage.getItem('status') !== 'visited') {
		countapi.update('wizzy-wig.netlify.app', countKey, 1)
			.then((result) => {
				const ordinal = getOrdinal(result.value);
				console.log(`congratulations, you are the ${ordinal} unique visitor`);
			});
	} else {
		countapi.get('wizzy-wig.netlify.app', countKey)
			.then((result) => {
				console.log(`this page has had ${result.value} unique visit${result.value !== 1 ? 's' : ''}`);
			});
	}
	
	// uncomment to reset counter
	// countapi.set('wizzy-wig.netlify.app', countKey, 0)
	//   .then((result) => {
	//     console.log(result);
	//   });
	
	localStorage.setItem('status', 'visited');
}, []);

```