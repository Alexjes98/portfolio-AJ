<script lang="ts">  
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
  export let isActive = false;
  export let rotationSpeed = 0.1;

  useTask((delta) => {
    if (isActive) rotation[orientation] += delta * rotationSpeed;
  });
</script>

<T.Group scale={$scale} {...$$restProps} bind:this={$component}>
  <Model
    scale={size}
    {position}
    {rotation}
    on:pointerenter={onPointerEnter}
    on:pointerleave={onPointerLeave}
    {component}
  />
</T.Group>
