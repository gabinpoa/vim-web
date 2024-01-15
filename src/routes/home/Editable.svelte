<script lang="ts">
	import { contentStore } from '$lib/stores';

	let content: string;

	contentStore.subscribe((value) => {
		content = value;
	});
</script>

<div
	bind:innerText={content}
	tabindex="0"
	contenteditable
	role="textbox"
	aria-multiline="true"
></div>
<pre class="block">
  <code class="block" contenteditable bind:innerText={content}/>
</pre>

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
