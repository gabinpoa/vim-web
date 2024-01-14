<script lang="ts">
	import { contentStore } from '$lib/stores';
	let content: string;

	contentStore.subscribe((value) => {
		content = value;
	});

	function handleKeyDown(event: KeyboardEvent) {
		if (event.key === 'h') {
			console.log('left');
		} else if (event.key === 'l') {
			console.log('right');
		} else if (event.key === 'j') {
			console.log('down');
		} else if (event.key === 'k') {
			console.log('up');
		}
	}
</script>

<div
	bind:innerText={content}
	tabindex="0"
	contenteditable
	role="textbox"
	aria-multiline="true"
	on:keydown={handleKeyDown}
></div>
<button
	type="button"
	on:click={() => {
		save(content);
	}}
>
	Save
</button>

<style>
	div {
		border: 1px solid #ccc;
		padding: 10px;
		min-height: 200px;
		margin-bottom: 10px;
		font-family: 'Courier New', monospace;
		font-size: 14px;
		white-space: pre-wrap;
	}
</style>
