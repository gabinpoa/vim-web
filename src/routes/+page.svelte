<script lang="ts">
	let files: FileList;
	function handleFileOpen() {
		const selectecFile = files.length === 1 ? files[1] : null;

		if (selectecFile) {
			const reader = new FileReader();
			reader.onload = () => {
				reader.readAsArrayBuffer(selectecFile);
			};
		}
	}
</script>

<form>
	<label for="file">Open a text based file</label>
	<input on:change={handleFileOpen} name="value" bind:files type="file" />
</form>
