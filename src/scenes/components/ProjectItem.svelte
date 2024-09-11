<script>  
  import { MeshLineGeometry, MeshLineMaterial } from "@threlte/extras";
  import { forwardEventHandlers, T, useTask } from "@threlte/core";
  import { useCursor, ImageMaterial } from "@threlte/extras";
  import { DoubleSide } from "three";
  import { spring } from "svelte/motion";
  import { Vector3, CatmullRomCurve3, Color } from "three";
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

  let width = 0.5
  let dashOffset = 0
  let color = new Color()
  const blue = new Color('#0000ff')
  const red = new Color('#ff0000')

  useTask((delta) => {
    // every frame we:
    // increase the dash offset
    dashOffset += delta / 2
    // transition between two colors
    color.lerpColors(blue, red, Math.sin(dashOffset * 2) / 2 + 0.5)
    // shrink and grow the line width
    width = Math.sin(dashOffset * 2) / 5 + 0.3
  })
</script>

<T.Group scale={$scale} {...$$restProps} bind:this={$component}>
  <T.Mesh receiveShadow position={[position[0]-2,position[1] -40,position[2]]}>
    <T.BoxGeometry args={[1, 100, 25]} />
    <T.MeshStandardMaterial color="white" />
  </T.Mesh>

  <T.Mesh receiveShadow position={[
    position[0] - 1,
    position[1] + 7,
    position[2]]}>
    <T.BoxGeometry args={[10, 1, 40]} />
    <T.MeshStandardMaterial color="white" />
  </T.Mesh>
  
  <T.Mesh>
    <MeshLineGeometry
      points={[
        new Vector3(position[0]-1,position[1]+ 6,position[2] +10),
        new Vector3(position[0]-1,position[1]+ -10,position[2] +10),
        new Vector3(position[0]-1,position[1]+ -10,position[2] +5),
        new Vector3(position[0]-1,position[1]+ 6,position[2] +5),
        new Vector3(position[0]-1,position[1]+ 0,position[2] -5),
        new Vector3(position[0]-1,position[1]+ -25,position[2] -5),
        new Vector3(position[0]-1,position[1]+ -25,position[2] +5),
        new Vector3(position[0]-1,position[1]+ 7,position[2] +5),
        new Vector3(position[0]-1,position[1]+ 7,position[2] +0),
        new Vector3(position[0]-1,position[1]+ -25,position[2] +0),
      ]}
      shape={"taper"}
    />
    <MeshLineMaterial width={0.1} color={color} dashArray={0.1} dashOffset={dashOffset} />
  </T.Mesh>
  <T.PointLight
    position={[position[0]-1, position[1]+6, position[2]]}
    castShadow
    intensity={100}
    color="purple"
    distance={100}
    decay={2}
  />
  <T.Mesh {position} {rotation} scale={geometry}>
    <T.PlaneGeometry />
    <ImageMaterial transparent side={DoubleSide} {url} radius={0.1} />
  </T.Mesh>
  {#each items as item, index}
    <T.Mesh
      position={[
        position[0] + 1 - index * 0.2,
        position[1] - 6,
        position[2] + index * -3.1 + 10,
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
