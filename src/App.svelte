<script>
  import Header from "./components/Header.svelte";
</script>

<main>
  <div class="landing-page">
    <Header headerText="Hi, I'm James..." />
  </div>
</main>

<style>
  .landing-page {
    display: flex;
    flex-flow: column wrap;
    align-items: flex-start;
    height: 100vh;
  }
</style>
