<script>
  export let imageData;
</script>

<div class="image_edit_view">
 {#if !imageData} 
   <p class="no_image">イメージファイルを指定してください</p>
 {:else}
   <img  src="{imageData}" alt="" />
 {/if}
</div>

<style>
  .image_edit_view {
    width: 600px;
    height: 600px;
    background: #d3d3d3;
    overflow: auto;
  }
  .no_image {
    font-size: 1em;
    font-weight: bold;
    text-align: center;
    margin-top: 200px;
  }
</style>