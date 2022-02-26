<script>
	import ImageEditView from "./components/ImageEditView.svelte"
	import ImageEditControl from "./components/ImageEditControl.svelte"

	// image data which read from file
	let imageData;
	// canvas context
	let context;
	// Image object 
	let image_obj;
	// canvas
	let image_canvas;

	// Called when image file is read in ImageEditControl
	const readImage = (e) => {
		imageData = e.detail.image;
		// console.log("set image", imageData)
	}

	// Called  when image is displayed in ImageEditView
	const displayImage = (e) => {
		context = e.detail.context;
		image_obj = e.detail.image_obj;
		image_canvas = e.detail.image_canvas;
		// console.log("set image", imageData)
	}
</script>

<main>
	<h1>ImageEdit</h1>
	<div class="main_view">
		<ImageEditView imageData={imageData} context={context} image_obj={image_obj} image_canvas={image_canvas} on:displayImage={displayImage}/>
		<ImageEditControl imageData={imageData} context={context} image_obj={image_obj} image_canvas={image_canvas} on:readImage={readImage}/>
	</div>
	<div class="credit">Created by go.hosohara@gmail.com</div>
</main>

<style>
	main {
		padding: 1em;
		width: 800px;
		margin: 0 auto;
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
		border: solid 1px black;
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