## ts/js

```ts
export function narcissistic(value: number): boolean {
	const splitNum = Array.from(String(value), Number);
	const summed = splitNum.reduce((a, b) => a += b ** splitNum.length, 0);
	
	return value === summed;
}
```

```ts
export class Kata {
  static highAndLow(numbers: string): string {
    const nums = numbers.split(' ').map(Number);
    
    return `${Math.max(...nums)} ${Math.min(...nums)}`
  }
}
```

```js
const mismaDiferencia = (arr) => {
    const findDif = (num1, num2) => {
        return parseFloat(Math.abs(num1 - num2).toFixed(2));
    }
	  
    const diferencia = findDif(arr[0], arr[1]);
    
    for (let i = 1; i < arr.length - 1; i++) {
        const currDiff = findDif(arr[i], arr[i + 1]);
        if (currDiff !== diferencia) return false;
    }
    
    return true;
}
```

```ts
export function SeriesSum(n: number) {
	let sum = 0;
	for (let i = 0; i < n; i++) {
	  sum += 1 / (1 + (3 * i));
	}
	
	return sum.toFixed(2);
}
```
