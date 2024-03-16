<script>
  import LineChart from "./LineChart.svelte";
  import { onMount } from "svelte";

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

<h2>Development of my coding skills overtime.</h2>
<section class="container">
  {#if viewport === "desktop"}
    <svelte:component
      this={CHART_TYPES[type]}
      {...chartProps}
      chartWidth={800}
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

<style>
  .container {
    max-width: 800px;
    margin: auto;
  }

  h2 {
    text-align: center;
    padding: 2rem;
    margin: 2rem;
  }
</style>
