<script>
  import MediaQuery from "svelte-media-queries";
  export let headerText;

  let log = 0;

  let dotA = "";
  let dotB = "";
  let dotC = "";

  const addDot = () => {
    if (log === 0) {
      dotA = ".";
      log++;
    } else if (log === 1) {
      dotB = ".";
      log++;
    } else if (log === 2) {
      dotC = ".";
      log++;
    } else {
      dotA = "";
      dotB = "";
      dotC = "";
      log = 0;
    }
  };

  setInterval(addDot, 700);
</script>

<MediaQuery query="(min-width: 1281px)" let:matches>
  {#if matches}
    <h1 class="poppins-bold">
      {headerText}<span>{dotA}</span><span style=";color: var(--secondary)"
        >{dotB}</span
      ><span style=";color: var(--tertiary)">{dotC}</span>
    </h1>
  {/if}
</MediaQuery>

<MediaQuery query="(min-width: 481px) and (max-width: 1280px)" let:matches>
  {#if matches}
    <h1 class="poppins-bold tab-font">
      {headerText}<span>{dotA}</span><span style=";color: var(--secondary)"
        >{dotB}</span
      ><span style=";color: var(--tertiary)">{dotC}</span>
    </h1>
  {/if}
</MediaQuery>

<MediaQuery query="(max-width: 480px)" let:matches>
  {#if matches}
    <h1 class="poppins-bold mob-font">
      {headerText}<span>{dotA}</span><span style=";color: var(--secondary)"
        >{dotB}</span
      ><span style=";color: var(--tertiary)">{dotC}</span>
    </h1>
  {/if}
</MediaQuery>

<style>
  h1 {
    text-align: left;
    font-size: 4rem;
    margin: 2rem 2rem 1rem 2rem;
    padding: 1rem;
  }

  .mob-font {
    font-size: 2rem !important;
  }

  .tab-font {
    font-size: 2.5rem !important;
  }

  span {
    font-size: 4rem;
  }
</style>
