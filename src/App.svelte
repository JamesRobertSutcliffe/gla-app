<script>
  import Character from "./components/Character.svelte";
  import ChartContainer from "./components/ChartContainer.svelte";
  import Header from "./components/Header.svelte";
  import LowerText from "./components/LowerText.svelte";
  import Map from "./components/Map.svelte";
  import Skills from "./components/Skills.svelte";
  import { skills } from "./data/skillTime";
  import gitHub from "../src/images/github.png";
  import net from "../src/images/net.png";
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
  <div class="page height">
    <div class="width-90">
      <Header headerText="Projects" />
      <p>
        Please take a look at my pinned <a
          href="https://github.com/JamesRobertSutcliffe"
          target="_blank"><span>github</span></a
        >
        projects to see examples of my reactive coding projects including the code
        for
        <a
          href="https://github.com/JamesRobertSutcliffe/gla-app"
          target="_blank">this page</a
        >
        <span>(Svelte, D3.js)</span>,
        <a
          href="https://wordle-mreu-gc7magqvl-jamesrobertsutcliffe.vercel.app/"
          target="_blank">Worldle Clone</a
        ><span>(React)</span>,
        <a href="https://react-todo-list-tau-orpin.vercel.app/" target="_blank"
          >React To Do List</a
        ><span>(React)</span>,
        <a
          href="https://personality-music-recommender-jer1.vercel.app/"
          target="_blank">Personality Music Recommender</a
        >
        - WORK IN PROGRESS<span>(next.js, SQL, Typescript)</span>,
        <a
          href="https://main--guileless-dragon-49c84e.netlify.app/"
          target="_blank">Cockney AI Chatbot</a
        >
        and
        <a href="http://18.170.214.75:3000/" target="_blank">Travel Mashup</a>
        <span>(HTML, CSS, JS, Open AI API).</span>
        <br /> <br />
        Please also take a look at my
        <a
          href="https://jamesrobertsutcliffe.github.io/js-portfolio/"
          target="_blank"><span>portfolio</span></a
        > to find out more about me and see some more of my projects.
      </p>
      <div class="center">
        <a href="https://github.com/JamesRobertSutcliffe" target="_blank">
          <img src={gitHub} alt="GitHub Logo" />
        </a>
        <a
          href="https://jamesrobertsutcliffe.github.io/js-portfolio/"
          target="_blank"
        >
          <img src={net} alt="GitHub Logo" />
        </a>
      </div>
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

  .height {
    height: auto !important;
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

  p {
    text-align: justify;
    width: 70%;
    margin: auto;
    text-justify: inter-word;
  }

  span {
    font-weight: 800;
  }

  img {
    width: 12rem;
    transition: 0.5s;
    margin: 2rem;
    padding: 2rem;
  }

  img:hover {
    scale: 110%;
  }
</style>
