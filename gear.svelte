<!--
Auto-generated by: https://github.com/threlte/threlte/tree/main/packages/gltf
Command: npx @threlte/gltf@2.0.3 gear.glb
-->

<script>
  import { Group } from 'three'
  import { T, forwardEventHandlers } from '@threlte/core'
  import { useGltf } from '@threlte/extras'

  export const ref = new Group()

  const gltf = useGltf('/gear.glb')

  const component = forwardEventHandlers()
</script>

<T is={ref} dispose={false} {...$$restProps} bind:this={$component}>
  {#await gltf}
    <slot name="fallback" />
  {:then gltf}
    <T.Mesh
      geometry={gltf.nodes.mesh_0.geometry}
      material={gltf.nodes.mesh_0.material}
      position={[3.19, 0, 6.12]}
      rotation={[-Math.PI / 2, 0, 0]}
    />
  {:catch error}
    <slot name="error" {error} />
  {/await}

  <slot {ref} />
</T>
