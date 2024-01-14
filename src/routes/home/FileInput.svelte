<script lang="ts">
	import { contentStore } from '$lib/stores';
	let files: FileList | undefined;

	$: if (files) {
		const selectecFile = files[0] || null;
		if (selectecFile) {
			const reader = new FileReader();
			reader.onload = (event) => {
				contentStore.update((oldValue) => (event.target?.result as string) || oldValue);
			};
			reader.readAsText(selectecFile);
		}
	}
</script>

<form>
	<label for="file">Open a text based file</label>
	<input name="value" bind:files type="file" />
</form>
