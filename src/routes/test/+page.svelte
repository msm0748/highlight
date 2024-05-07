<script>
	let listItems;

	function markText() {
		const items = Array.from(listItems.children);
		items.forEach((item) => {
			const text = item.textContent;
			if (text.includes('세요111')) {
				const markedText = text.replace('세요111', '<mark>세요111</mark>');
				item.innerHTML = markedText;
			}
		});
	}
</script>

<ul bind:this={listItems}>
	<li>안녕하세요111</li>
	<li>안녕하세요2222</li>
</ul>

<button on:click={markText}>Mark Text</button>
