<script lang="ts">
  import { Canvas } from "@threlte/core";
  import { Environment } from "@threlte/extras";

  import HomeScene from "../scenes/homeScene.svelte";
  import ExperienceList from "../components/experienceList.svelte";
  import PresentationSection from "../components/presentationSection.svelte";
  import AboutMe from "../components/aboutMe.svelte";
  import JourneyResume from "../components/journeyResume.svelte";
  import SkillsList from "../components/skillsList.svelte";
</script>

<main>
  <div class="canvas">
    <Canvas>
      <HomeScene />
    </Canvas>
  </div>
  <div class="content">
    <PresentationSection />
    <ExperienceList />
      <AboutMe />
      <JourneyResume />
      <SkillsList />
  </div>
</main>

<style>

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
