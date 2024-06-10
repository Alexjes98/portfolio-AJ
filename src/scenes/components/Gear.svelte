<script lang="ts">
  import { forwardEventHandlers, T, useTask } from "@threlte/core";
  import { useCursor } from "@threlte/extras";
  import { spring } from "svelte/motion";
  const scale = spring(1);
  const component = forwardEventHandlers();
  const { onPointerEnter, onPointerLeave } = useCursor();
  export let color = "red";
  export let position = [0, 0, 0];
  export let rotation = [0, 0, 0];
  export let geometry = [1, 1, 1];
  export let lights: any[] = [];
  export let isActive = false;
  export let rotationSpeed = 0.1;

  useTask((delta) => {
    if (isActive) rotation[1] += delta * rotationSpeed;
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
      color={"blue"}
    />
  {/each}
  <T.PointLight
    position={[position[0] + geometry[0] , position[1], position[2]]}
    {rotation}
    intensity={100}
    color={"blue"}
  />
  <T.PointLight
    position={[position[0] - geometry[0], position[1], position[2]]}
    {rotation}
    intensity={100}
    color={"blue"}
  />
  <T.PointLight
    position={[position[0], position[1], position[2] + geometry[2]]}
    {rotation}
    intensity={100}
    color={"blue"}
  />
  <T.PointLight
    position={[position[0], position[1], position[2] - geometry[2]]}
    {rotation}
    intensity={100}
    color={"blue"}
  />
  <T.PointLight
    position={[position[0], position[1] + geometry[1], position[2]]}
    {rotation}
    intensity={100}
    color={"blue"}
  />
  <T.Mesh
    castShadow
    receiveShadow
    {position}
    rotation={[rotation[0], rotation[1], rotation[2]]}
    on:pointerenter={onPointerEnter}
    on:pointerleave={onPointerLeave}
  >
    <T.CylinderGeometry args={geometry} />
    <T.MeshStandardMaterial {color} />
  </T.Mesh>
</T.Group>
