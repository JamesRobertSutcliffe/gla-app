<script>
  export let chartWidth;
  export let chartHeight;
  const paddings = {
    top: 50,
    left: 50,
    right: 50,
    bottom: 50,
  };

  // Renders points to x and y axis

  import { scaleLinear } from "d3";

  export let data;
  export let xVar;
  export let yVars;
  const xScale = scaleLinear()
    .domain([
      Math.min(...data.map((d) => d[xVar])),
      Math.max(...data.map((d) => d[xVar])),
    ])
    .range([paddings.left, chartWidth - paddings.right]);
  const yScale = scaleLinear()
    .domain([
      Math.min(...data.map((d) => Math.min(...yVars.map((yVar) => d[yVar])))),
      Math.max(...data.map((d) => Math.max(...yVars.map((yVar) => d[yVar])))),
    ])
    .range([chartHeight - paddings.bottom, paddings.top])
    .nice(10);

  // Displays date across X in correct format

  const formatFunction = (x) => {
    const date = new Date(x);
    return `${date.getMonth() + 1}-${date.getFullYear()}`;
  };

  //Ticks

  import Tick from "./Tick.svelte";
  const tickNumber = chartWidth > 480 ? 10 : 5;
  const yGrid = yScale.ticks(10);
  const xGrid = xScale.ticks(tickNumber);
</script>

<svg width={chartWidth} height={chartHeight}>
  <g>
    {#each yGrid.slice(1) as gridLine}
      <Tick
        x={paddings.left}
        y={yScale(gridLine)}
        value={gridLine}
        direction={"horizontal"}
        formatFunction={undefined}
      />
    {/each}
  </g>
  <g>
    {#each xGrid as gridLine}
      <Tick
        x={xScale(gridLine)}
        y={chartHeight - paddings.bottom}
        value={gridLine}
        direction={"vertical"}
        format={false}
        {formatFunction}
      />
    {/each}
  </g>
  <g>
    <line
      x1={paddings.left}
      x2={chartWidth - paddings.right}
      y1={chartHeight - paddings.bottom}
      y2={chartHeight - paddings.bottom}
      stroke="black"
      stroke-width="2"
    />
    <line
      x1={paddings.left}
      x2={paddings.left}
      y1={paddings.top}
      y2={chartHeight - paddings.bottom}
      stroke="black"
      stroke-width="2"
    />
    {#each data as datum, i}
      {#each yVars as yVar}
        {#if i != data.length - 1}
          <line
            x1={xScale(data[i][xVar])}
            x2={xScale(data[i + 1][xVar])}
            y1={yScale(data[i][yVar])}
            y2={yScale(data[i + 1][yVar])}
            stroke="#178eb3"
            stroke-width="2"
          />
        {/if}
      {/each}
    {/each}
  </g>
</svg>
