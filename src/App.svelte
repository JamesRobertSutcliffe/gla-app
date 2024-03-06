<script>
  import Character from "./components/Character.svelte";
  import Header from "./components/Header.svelte";
  import LowerText from "./components/LowerText.svelte";
</script>

<main>
  <div class="landing-page">
    <div class="width-90">
      <Header headerText="Hi, I'm James..." />
    </div>
    <div class="center">
      <Character />
    </div>
    <div class="center width-90">
      <LowerText />
    </div>
  </div>
</main>

<style>
  .landing-page {
    display: flex;
    flex-flow: column;
    height: 100vh;
    justify-content: space-evenly;
  }

  .center {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
  }

  .width-90 {
    width: 90%;
    margin: auto;
  }
</style>
