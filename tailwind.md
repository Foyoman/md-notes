- tailwind.config.js
	- content
	- theme

```jsx
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer base { 
	h1 { 
		@apply text-2xl; 
	} 
	h2 { 
		@apply text-xl; 
	} 
	/* ... */ 
}

@layer components { 
	.card { 
		background-color: theme('colors.white'); 
		border-radius: theme('borderRadius.lg'); 
		padding: theme('spacing.6'); 
		box-shadow: theme('boxShadow.xl'); 
	} 
	/* ... */ 
}

@layer utilities
```

- @layer
- customisation
	- tailwind.config.js, theme, extend, colour, spacing
- plugin
- arbitrary values