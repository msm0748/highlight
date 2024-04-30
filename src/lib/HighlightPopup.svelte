<script>
	export let position;

	console.log(position);
</script>

<div class="popup-bubble-option" style="top: {position.y - 135}px; left: {position.x}px">
	<button class="popup-bubble-button">highlight</button>
	<a class="popup-bubble-button" href="/test" target="_blank">Google Search</a>
</div>

<style lang="scss">
	.popup-bubble-option {
		position: absolute;
		z-index: 1000;
		background-color: #fff;
		display: flex;
		flex-direction: column;
		border: 1px solid #eceef0;
		border-radius: 6px;
		width: 320px;
		padding: 3px 0;

		box-shadow: 0px 10px 15px -3px #00000014;
		// box-shadow: 0px 4px 6px -2px #00000005;

		.popup-bubble-button {
			text-align: left;
			display: block;
			font-size: 26px;
			line-height: 36px;
			padding: 12px 20px;
			font-weight: 400;
		}
	}
</style>
