<script>
  import Timer from "./Timer.svelte";
  import HowTo from "./HowTo.svelte";
  let audio;
  function timerEnds() {
    audio.play();
  }
</script>

<style>
  h1,
  h3 {
    text-align: center;
  }
  h3 a {
    margin: 0 10px;
  }
</style>

<h1>Handwashing App</h1>
<Timer on:end={timerEnds} />
<HowTo />
<h3>
  <a href="https://www.who.int/gpsc/clean_hands_protection/en/">
    Picture Source
  </a>
  <a href="https://freesound.org/people/javapimp/sounds/439017/">
    Sound Source
  </a>
</h3>
<audio bind:this={audio} src="sound.wav" />
