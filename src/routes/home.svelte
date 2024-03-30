<script lang="ts">
  import { Canvas } from "@threlte/core";
  import HomeScene from "../scenes/homeScene.svelte";
  import ExperienceList from "../components/experienceList.svelte";
  import PresentationSection from "../components/presentationSection.svelte";
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
    margin-top: 80px;
    z-index: 1;
  }
</style>
