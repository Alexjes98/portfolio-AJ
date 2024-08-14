<script lang="ts">
  import { MeshBasicMaterial } from "three";
  import { forwardEventHandlers, T, useTask } from "@threlte/core";
  import { useCursor } from "@threlte/extras";
  import { spring } from "svelte/motion";

  import Model from "../../../gear.svelte";
  const scale = spring(1);
  const component = forwardEventHandlers();
  const { onPointerEnter, onPointerLeave } = useCursor();
  export let position = [0, 0, 0];
  export let rotation = [0, 0, 0];
  export let orientation = 1;
  export let size = [1, 1, 1];
  export let lights: any[] = [];
  export let isActive = false;
  export let rotationSpeed = 0.1;

  useTask((delta) => {
    if (isActive) rotation[orientation] += delta * rotationSpeed;
  });
</script>

<T.Group scale={$scale} {...$$restProps} bind:this={$component}>
  {#each lights as light}
    <T.PointLight
      position={[
        position[0] + light.position[0],
        position[1] + light.position[1],
        position[2] + light.position[2],
      ]}
      {rotation}
      intensity={light.intensity}
      color={"darkblue"}
    />
  {/each}
  <T.PointLight
    position={[position[0] + size[0], position[1], position[2]]}
    {rotation}
    intensity={100}
    color={"darkblue"}
  />
  <T.PointLight
    position={[position[0] - size[0], position[1], position[2]]}
    {rotation}
    intensity={10}
    color={"darkblue"}
  />
  <T.PointLight
    position={[position[0], position[1], position[2] + size[2]]}
    {rotation}
    intensity={10}
    color={"darkblue"}
  />
  <T.PointLight
    position={[position[0], position[1], position[2] - size[2]]}
    {rotation}
    intensity={10}
    color={"darkblue"}
  />
  <T.PointLight
    position={[position[0], position[1] + size[1], position[2]]}
    {rotation}
    intensity={10}
    color={"darkblue"}
  />
  <Model
    scale={size}
    {position}
    {rotation}
    on:pointerenter={onPointerEnter}
    on:pointerleave={onPointerLeave}
    {component}
  />
</T.Group>
