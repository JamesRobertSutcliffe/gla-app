<script>
  import Aside from "./Aside.svelte";
  import LineChart from "./LineChart.svelte";
  import { onMount } from "svelte";
  import { skillTimeText } from "../data/text";

  export let type;
  export let chartProps;
  const CHART_TYPES = {
    lineChart: LineChart,
  };

  let viewport = "mobile";

  function setViewportMq(_) {
    viewport =
      window.innerWidth >= 768
        ? "desktop"
        : window.innerWidth >= 480
          ? "tablet"
          : "mobile";
  }

  onMount(() => {
    if (typeof window !== "undefined") {
      window.addEventListener("resize", setViewportMq);
      setViewportMq();
    }
  });
</script>

<h2>Development of my coding skills over time.</h2>
<div class="center">
  <div class="width-50">
    <Aside text={skillTimeText} />
  </div>
  <section class="container">
    {#if viewport === "desktop"}
      <svelte:component
        this={CHART_TYPES[type]}
        {...chartProps}
        chartWidth={750}
        chartHeight={500}
      />
    {:else if viewport === "tablet"}
      <svelte:component
        this={CHART_TYPES[type]}
        {...chartProps}
        chartWidth={480}
        chartHeight={375}
      />
    {:else}
      <svelte:component
        this={CHART_TYPES[type]}
        {...chartProps}
        chartWidth={window.innerWidth * 0.9}
        chartHeight={window.innerWidth * 0.9 * 0.78}
      />{/if}
  </section>
</div>

<style>
  .container {
    max-width: 700px;
    margin: 1rem;
  }

  h2 {
    text-align: center;
    /* padding: 2rem; */
    /* margin: 2rem; */
  }

  .center {
    display: flex;
    flex-flow: row wrap;
    justify-content: space-evenly;
    align-items: center;
    height: 75vh;
  }

  .width-50 {
    width: 40%;
  }
</style>
