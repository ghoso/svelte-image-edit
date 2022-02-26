<script>
  // image data which is read from file 
  export let image;
  // canvas context
  export let context;
  // Image object
  export let image_obj;
  // Canvas
  export let image_canvas;
  
  const flipImage = (e, ctx, img_data, img_obj, direction) => {
    // console.log("flipImage: direction =", direction)
    let angle = 0
    // select which direction image rotate
    if (direction === "left"){
       angle = -90*Math.PI/180
    } else if (direction === "right"){
       angle = 90*Math.PI/180
    } else {
      return
    }
   
    // Rotate image
    ctx.clearRect(0, 0, image_canvas.width, image_canvas.height)
    ctx.translate(image_canvas.width/2, image_canvas.height/2);
    ctx.rotate(angle);
    ctx.drawImage(img_obj, -(img_obj.width/2), -(img_obj.height/2), img_obj.width, img_obj.height);
    ctx.translate(-image_canvas.width/2, -image_canvas.height/2);
  }
</script>

<div class="flip_control">
  <button class="flip_button" on:click={(e) => flipImage(e, context, image, image_obj, "left")}>左90°</button>
  <button class="flip_button" on:click={(e) => flipImage(e, context, image, image_obj, "right")}>右90°</button>
</div>

<style>
  .flip_control {
    display: flex;
    flex-direction: row;
    margin: 10px auto; 
  }
  
  .flip_button {
    margin: 0 10px;
  }
</style>