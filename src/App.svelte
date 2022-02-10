<script>
	import ImageEditView from "./components/ImageEditView.svelte"
	import ImageEditControl from "./components/ImageEditControl.svelte"
</script>

<main>
	<h1>ImageEdit</h1>
	<div class="main_view">
		<ImageEditView />
		<ImageEditControl />
	</div>
	<div class="credit">Created by go.hosohara@gmail.com</div>
</main>

<style>
	main {
		padding: 1em;
		width: 800px;
		margin: 0 auto;
		border: solid 1px black;
	}

	h1 {
		text-align: center;
		color: #ff3e00;
		font-size: 4em;
		font-weight: 100;
	}

	.main_view {
		display: flex;
		flex-direction: row;
		margin: auto 0;
	}
	
	.credit {
		margin: 10px;
		text-align: center;
		color: #a9a9a9;
	}
	
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>