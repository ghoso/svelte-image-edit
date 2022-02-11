<script>
const flipImage = (e, direction) => {
  
}
</script>

<div class="flip_control">
  <button class="flip_button" on:click={(e) => flipImage(e, "left")}>左90°</button>
  <button class="flip_button" on:click={(e) => flipImage(e, "right")}>右90°</button>
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