<script lang="ts">
  import { Canvas } from "@threlte/core";
  import HomeScene from "../scenes/homeScene.svelte";
</script>

<main>
  <div class="canvas">
    <Canvas>
      <HomeScene />
    </Canvas>
  </div>
  <div class="content">
    <h1>Hi my name is Alejandro Lopez</h1>
    <h2>I'm a software engineer with a passion for system design.</h2>
  </div>
</main>

<style>
  .canvas {
    position: absolute;
    z-index: -1;
    width: 100%;
    height: 100%;
  }

  .content {
    position: relative;
    margin-top: 80px;
    z-index: 1;
  }
</style>
