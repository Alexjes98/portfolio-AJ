<script lang="ts">
  
  import { Canvas } from "@threlte/core";

  import HomeScene from "../scenes/homeScene.svelte";
  import ExperienceList from "../components/experienceList.svelte";
  import PresentationSection from "../components/presentationSection.svelte";
  import AboutMe from "../components/aboutMe.svelte";
  import JourneyResume from "../components/journeyResume.svelte";
  import SkillsList from "../components/skillsList.svelte";
  import ProjectsList from "../components/projectsList.svelte";
  import Contact from "../components/contact.svelte";

  window.onscroll = function () {
    var docHeight =
      document.documentElement.scrollHeight -
      document.documentElement.clientHeight;
    var scrollPosition =
      window.screenY ||
      document.documentElement.scrollTop ||
      document.body.scrollTop ||
      0;
    var scrollPercentage = (scrollPosition / docHeight) * 100;

    var element = document.getElementById("progressBar") || document.createElement("div");

    element.style.width = scrollPercentage + "%";
  };
</script>

<main>
  <div id="progressBar"></div>
  <div class="canvas">
    <Canvas>
      <HomeScene />
    </Canvas>
  </div>
  <div class="content">
    <PresentationSection />
    <ExperienceList />
    <ProjectsList />
    <AboutMe />
    <JourneyResume />
    <SkillsList />
    <Contact />
  </div>
</main>

<style>
  #progressBar {
    position: fixed;
    top: 0;
    left: 0;
    width: 0;
    height: 5px;
    background: blue;
    z-index: 100;
  }
  .canvas {
    position: fixed;
    z-index: -1;
    width: 100%;
    height: 100%;
  }

  .content {
    margin-top: 20px;
    z-index: 1;
  }
</style>
