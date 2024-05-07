<script>
	import Mark from 'mark.js';
	import { onMount } from 'svelte';

	let instance;

	onMount(() => {
		instance = new Mark(document.querySelector('div'));
	});

	function markText() {
		const textContent = document.querySelector('p').textContent;
		const keyword1 = '안녕하세요';
		const keyword2 = '잘 부탁드립니다.';
		const startIndex1 = textContent.indexOf(keyword1);
		const startIndex2 = textContent.indexOf(keyword2);

		// if (startIndex1 !== -1 && startIndex2 !== -1) {
		// 	const endIndex1 = startIndex1 + keyword1.length;
		// 	const endIndex2 = startIndex2 + keyword2.length;
		const options = {
			acrossElements: true,
			separateWordSearch: false,
			accuracy: 'exactly',
			element: 'mark',
			className: 'highlight'
		};

		instance.unmark();
		instance.markRanges(
			[
				{ start: startIndex1, length: keyword1.length },
				{ start: startIndex2, length: keyword2.length }
			],
			options
		);
		// }
	}
</script>

<p>안녕하세요 저는 ooo입니다. 잘 부탁드립니다.</p>
<button on:click={markText}>Mark Text</button>
