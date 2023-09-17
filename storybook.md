## Boilerplate for new component

```jsx
<template>
	<div class="container mds__component" v-editable="this.$props">
		hello, world
	</div>
</template>

<script>
export default {
	// ...
}
</script>

<style lang="scss" scoped>
</style>
```

```jsx
import MdsNewComponent from "~/components/NewComponent/NewComponent.vue";
import { ArgsTable, Canvas, Meta, Story } from "@storybook/addon-docs";

<Meta
	title="NewComponent/NewComponent"
	component={MdsNewComponent}
	argTypes={{
		// ...
	}}
/>

# NewComponent

A NewComponent

export const NewComponentTemplate = (args, { argTypes }) => ({
	props: Object.keys(args),
	components: { MdsNewComponent },
	template: `<MdsNewComponent v-bind="$props" />`
});

<Canvas>
	<Story
		name="Overview"
		parameters={{
			docs: {
				source: {
					type: "dynamic",
					format: true,
				},
			},
	  }}
		args={{
			// ...
		}}
  >
		{NewComponentTemplate.bind({})}
	</Story>
</Canvas>

### Props & Slots

<ArgsTable story="Overview" />
```
