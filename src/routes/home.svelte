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

  function debounce(func: Function, wait: number) {
    let timeout: number | null = null;
    return function executedFunction(...args: any[]) {
      const later = () => {
        timeout = null;
        func(...args);
      };
      if (timeout) clearTimeout(timeout);
      timeout = window.setTimeout(later, wait);
    };
  }

  const updateProgressBar = debounce(() => {
    const docHeight = document.documentElement.scrollHeight - document.documentElement.clientHeight;
    const scrollPosition = window.screenY || document.documentElement.scrollTop || document.body.scrollTop || 0;
    const scrollPercentage = (scrollPosition / docHeight) * 100;

    const element = document.getElementById("progressBar");
    if (element) {
      element.style.width = scrollPercentage + "%";
    }
  }, 16); // Debounce at ~60fps

  window.onscroll = updateProgressBar;
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
