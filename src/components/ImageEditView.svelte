<script>
  import { createEventDispatcher } from "svelte"
  // image data which is read from file
  export let imageData;
  // canvas context
  export let context;
  // Image object
  export let image_obj;
  // canvas
  export let image_canvas;
  
  // load image file data
  const loadImage = (img_data) => { 
    if (!image_canvas || !image_canvas.getContext) {
      // console.log("no image_view");
      return false;
    }
    // console.log("imageData=", img_data);
    const dispatch = createEventDispatcher()
    context = image_canvas.getContext("2d");
    context.clearRect(0,0, image_canvas.width, image_canvas.height);
    image_obj = new Image();
    image_obj.src = img_data;
    dispatch("displayImage", {context: context, image_obj: image_obj, image_canvas: image_canvas}) 
    image_obj.onload = () =>{
      // set canvas size longer distance either width or height
      // and rotate canvas
      const cnvs_size = Math.max(image_obj.width, image_obj.height);
      const w_margin = (cnvs_size - image_obj.width)/2;
      const h_margin = (cnvs_size - image_obj.height)/2;
      image_canvas.width = cnvs_size;
      image_canvas.height = cnvs_size;
      
      context.drawImage(image_obj, w_margin, h_margin, image_obj.width, image_obj.height); 
    }
  }
 
  // called when image file is selected
  $: loadImage(imageData)
</script>

<div class="image_edit_view">
   <canvas class="image_canvas"  alt="" bind:this={image_canvas}></canvas>
</div>

<style>
  .image_edit_view {
    width: 600px;
    height: 600px;
    background: #d2d2d2;
    overflow: auto;
  }
  
</style>