<script>
  import { createEventDispatcher } from "svelte";
  import FlipControl from "./FlipControl.svelte"

  let fileinput;
  export let imageData;

  const dispatch = createEventDispatcher();

  const onFileSelected = (e) => {
    let image = e.target.files[0];
    //console.log("image file:", image)
    let reader = new FileReader();
    reader.readAsDataURL(image);
      reader.onload = e => {
      imageData = e.target.result;
      dispatch('readImage', { image: imageData });
    }
  }
</script>

<div class="edit_control">
  <div class="edit_control_label">ImageEdit</div>
  <button class="upload_control" 
       on:click={()=>{fileinput.click();}}>
       ファイル指定
  </button>
  <input type="file" 
         style="display: none"
         accept="image/*"
         on:change={(e)=>onFileSelected(e)}
         bind:this={fileinput}>
  <FlipControl />
  <div class="edit_control_label">拡大・縮小</div>
  <input type="range" class="slider" value="50" min="1" max="100" />
  <button class="control_btn">保存</button>
</div>

<style>
.upload_control {
  border: solid 1px black;
  width: 130px;
  margin: 10px auto;
}
.edit_control {
  width: 200px;
  height: 600px;
  display: flex;
  flex-direction: column;
}

.edit_control_label {
  font-size: 1.3em;
  font-weight: bold; 
  text-align: center;
  margin-top: 10px;
  margin-bottom: 10px;
}

.control_btn {
  margin: 10px 20px;
}

.slider {
  margin: 0 10px 10px 10px;
}
</style>