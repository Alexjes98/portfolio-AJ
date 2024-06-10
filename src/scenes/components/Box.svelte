<script lang="ts">
  import { forwardEventHandlers, T } from "@threlte/core";
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
</script>

<T.Group scale={$scale} {...$$restProps} bind:this={$component}>
  {#each lights as light}
    <T.PointLight
      position={[
        position[0] + light.position[0],
        position[1] + light.position[1],
        position[2] + light.position[2],
      ]}
      intensity={light.intensity}
      color={"blue"}
    />
  {/each}
  <T.Mesh
    castShadow
    receiveShadow
    {position}
    {rotation}
    on:pointerenter={onPointerEnter}
    on:pointerleave={onPointerLeave}
  >
    <T.BoxGeometry args={geometry} />
    <T.MeshStandardMaterial {color} />
  </T.Mesh>
</T.Group>
