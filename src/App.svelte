<script>
  import Character from "./components/Character.svelte";
  import ChartContainer from "./components/ChartContainer.svelte";
  import Header from "./components/Header.svelte";
  import LowerText from "./components/LowerText.svelte";
  import Map from "./components/Map.svelte";
  import Skills from "./components/Skills.svelte";
  import { skills } from "./data/skillTime";
</script>

<main>
  <div class="page">
    <div class="width-90">
      <Header headerText="Hi, I'm James" />
    </div>

    <div class="center">
      <Character />
    </div>

    <div class="center width-90">
      <LowerText />
    </div>
  </div>

  <div class="page">
    <div class="width-90">
      <Header headerText="Map" />
      <Map />
    </div>
  </div>

  <div class="page">
    <div class="width-90">
      <Header headerText="Skills" />
      <Skills />
    </div>
  </div>

  <div class="page">
    <div class="width-90">
      <Header headerText="Skills Over Time" />
      <ChartContainer
        type={"lineChart"}
        chartProps={{
          chartWidth: 800,
          chartHeight: 500,
          data: skills,
          xVar: "Year",
          yVars: ["Skill"],
        }}
      />
    </div>
  </div>
</main>

<style>
  .page {
    display: flex;
    flex-flow: column;
    height: 100vh;
    justify-content: space-around;
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
