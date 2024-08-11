<script>
  import { forwardEventHandlers, T } from "@threlte/core";
  import { useCursor, ImageMaterial } from "@threlte/extras";
  import { DoubleSide } from "three";
  import { spring } from "svelte/motion";
  const scale = spring(1);
  const component = forwardEventHandlers();
  const { onPointerEnter, onPointerLeave } = useCursor();

  export let position = [0, 0, 0];
  export let rotation = [0, 0, 0];
  export let geometry = [1, 1, 1];

  export let url = "";
  /**
   * @type {any[]}
   */
  export let items = [];
</script>

<T.Group scale={$scale} {...$$restProps} bind:this={$component}>
  <T.Mesh {position} {rotation} scale={geometry}>
    <T.PlaneGeometry />
    <ImageMaterial transparent side={DoubleSide} {url} radius={0.1} />
  </T.Mesh>
  {#each items as item, index}
    <T.Mesh
      position={[
        position[0] + 1 - (index) * 0.2,
        position[1] - 6,
        position[2] + ((index) * -3.1) + 10,
      ]}
      {rotation}
      scale={[3, 3, 3]}      
    >
      <T.PlaneGeometry />
      <ImageMaterial
        transparent
        side={DoubleSide}
        url={item.url}
        zoom={item?.zoom || 1}
        radius={0.1}
      />
    </T.Mesh>
  {/each}
</T.Group>
