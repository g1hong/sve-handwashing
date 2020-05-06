<script>
  import ProgressBar from "./ProgressBar.svelte";
</script>

<style>
  h2 {
    margin: 0;
  }
  .start {
    background-color: rgb(170, 73, 73);
    width: 100%;
    margin: 10px auto;
  }
</style>

<div bp="grid">
  <h2 bp="offset-5@lg 4@lg offset-4@md 6@md 12@sm">Seconds Left</h2>
</div>
<ProgressBar />

<button class="start">Start</button>
