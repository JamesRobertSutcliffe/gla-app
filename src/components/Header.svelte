<script>
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

<h1 class="poppins-bold">
  {headerText}<span>{dotA}</span><span style=";color: var(--secondary)"
    >{dotB}</span
  ><span style=";color: var(--tertiary)">{dotC}</span>
</h1>

<style>
  h1 {
    text-align: left;
    font-size: 4rem;
    margin: 2rem 2rem 1rem 2rem;
    padding: 1rem;
  }

  span {
    font-size: 4rem;
  }
</style>
