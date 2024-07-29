<script context="module" lang="ts">
	export const meta = {
		title: 'Bug',
	};
</script>

<script lang="ts">
	import { Story } from '@storybook/addon-svelte-csf';
	import { expect, userEvent, within, fn } from '@storybook/test';
</script>

<Story
	name="Default"
	let:args
	argTypes={{
		test: {
			action: 'inputRequired',
		},
	}}
	play={async ({ canvasElement, args }) => {
		const canvas = within(canvasElement);
		const button = canvas.getByRole('button');
		button.click();
		expect(args.test).toHaveBeenCalledTimes(1);
	}}
>
	<button on:click={() => args.test()}>Submit</button>
</Story>
