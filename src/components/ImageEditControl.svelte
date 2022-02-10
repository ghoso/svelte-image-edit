<script>
  import FlipControl from "./FlipControl.svelte"
</script>

<div class="edit_control">
  <div class="edit_control_label">ImageEdit</div>
  <button class="control_btn">ファイル選択</button>
  <FlipControl />
  <div class="edit_control_label">拡大・縮小</div>
  <input type="range" class="slider" value="50" min="1" max="100" />
  <button class="control_btn">保存</button>
</div>

<style>
.edit_control {
  width: 200px;
  height: 600px;
  display: flex;
  flex-direction: column;
}

.edit_control_label {
  font-size: 1.2em;
  font-weight: bold; 
  text-align: center;
  margin-bottom: 10px;
}

.control_btn {
  margin: 10px 20px;
}

.slider {
  margin: 0 10px 10px 10px;
}
</style>