<script>
  import { createEventDispatcher } from "svelte";
  import ProgressBar from "./ProgressBar.svelte";
  const totalSeconds = 5;
  let secondsLeft = totalSeconds;
  let perSecond = 100 / secondsLeft;
  $: progress = (totalSeconds - secondsLeft) * perSecond;

  const dispatch = createEventDispatcher();

  let isRunning = false;
  function startTimer() {
    secondsLeft = totalSeconds;
    isRunning = true;
    let timer = setInterval(() => {
      secondsLeft -= 1;
      if (secondsLeft === 0) {
        clearInterval(timer);
        isRunning = false;
        secondsLeft = totalSeconds;
        dispatch("end");
      }
    }, 1000);
  }
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
  .start[disabled] {
    background-color: rgb(214, 151, 151);
    cursor: not-allowed;
  }
</style>

<div bp="grid">
  <h2 bp="offset-5@lg 4@lg offset-4@md 6@md 12@sm">
    {secondsLeft} Seconds Left
  </h2>
</div>
<ProgressBar {progress} />
<div bp="grid">
  <button
    disabled={isRunning}
    on:click={startTimer}
    bp="offset-5@lg 4@lg offset-4@md 6@md 12@sm"
    class="start">
    Start
  </button>
</div>
