<script>
  import Model from "../../gear.svelte";

  import { T, useTask, useThrelte } from "@threlte/core";
  import { OrbitControls, interactivity, Grid } from "@threlte/extras";
  import { Vector3, CatmullRomCurve3, Color } from "three";

  import { Suspense, Text } from "@threlte/extras";

  import Box from "./components/Box.svelte";
  import Gear from "./components/Gear.svelte";
  import Nucleus from "./components/Nucleus.svelte";
  import FloorGrid from "./components/FloorGrid.svelte";

  const curve = new CatmullRomCurve3([
    new Vector3(0, 0, 0),
    new Vector3(10, 10, 10),
    new Vector3(18, 0, 0),
    new Vector3(10, 0, -2),
    new Vector3(-5, 0, -10),
    new Vector3(-5, 0, 0),
    new Vector3(-5, 19, 0),
    new Vector3(-15, 22, -20),
    new Vector3(10, 0, -50),
    new Vector3(31, 0, -30),
    new Vector3(14, 0, 60),
  ]);
  const maxScrollY = 30000;
  const points = curve.getPoints(maxScrollY);

  interactivity();

  let rotation = 0;
  useTask((delta) => {
    rotation += delta;
  });

  let cameraPosition = [0, 0, 0];

  let scrollY = 0;
  let isMobile = window.innerWidth < 768;
  let isLowEndDevice =
    window.innerWidth < 480 ||
    /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(
      navigator.userAgent
    );

  $: {
    scrollY = Math.floor(scrollY);
    if (isMobile) {
      if (scrollY < maxScrollY) {
        cameraPosition = [
          points[scrollY].x,
          points[scrollY].y,
          points[scrollY].z,
        ];
      }
    } else {
      if (scrollY < maxScrollY) {
        cameraPosition = [
          points[scrollY].x,
          points[scrollY].y,
          points[scrollY].z,
        ];
      }
    }
  }
  const mainLightIntensity = isMobile ? 500 : isLowEndDevice ? 700 : 1000;
  const geometrySegments = isLowEndDevice ? 8 : isMobile ? 12 : 15;
</script>

<svelte:window bind:scrollY />

<Suspense final>
  <!-- Lights -->
  <T.PointLight
    position={[0, -22, -30]}
    {rotation}
    intensity={mainLightIntensity}
    color={"purple"}
  />
  <T.PointLight
    position={[0, -23, 0]}
    {rotation}
    intensity={mainLightIntensity}
    color={"purple"}
  />
  <T.PointLight
    position={[-40, -23, -40]}
    {rotation}
    intensity={mainLightIntensity}
    color={"blue"}
  />
  <!-- Grids -->
  <Grid
    type="grid"
    position={[-8, 0, -40]}
    cellColor={"violet"}
    fadeStrength={0}
    infiniteGrid
    rotation={[0, Math.PI / 2, Math.PI / 2]}
  />
  <Grid
    type="grid"
    position={[5, 0, 15]}
    cellColor={"violet"}
    fadeStrength={0}
    rotation={[0, Math.PI / 2, Math.PI / 2]}
  />
  <Grid
    type="grid"
    position={[-45, 10, 5]}
    cellColor={"black"}
    cellSize={3}
    size={5}
    fadeStrength={4}
    backgroundColor={"black"}
    backgroundOpacity={1}
    backgroundAlpha={1}
    infiniteGrid
    rotation={[Math.PI / 2, 0, Math.PI / 2]}
  />
  <Grid
    type="grid"
    position={[15, 0, 0]}
    cellColor={"blue"}
    rotation={[Math.PI / 2, 0, Math.PI / 2]}
  />
  <Grid
    type="grid"
    position={[0, -30, 0]}
    cellColor={"black"}
    infiniteGrid
    backgroundColor={"purple"}
    backgroundOpacity={1}
    backgroundAlpha={1}
    cellSize={3}
    size={5}
    rotation={[0, 0, 0]}
  />
  <Grid
    type="grid"
    position={[0, -10, 0]}
    cellColor={"blue"}
    fadeStrength={0}
    size={1}
    rotation={[0, Math.PI / 2, 0]}
  />
  <T.PerspectiveCamera
    makeDefault
    position={cameraPosition}
    aspect={window.innerWidth / window.innerHeight}
    near={0.1}
  >
    <OrbitControls enableDamping target={[0, 0, 0]} />
  </T.PerspectiveCamera>

  <T.Mesh
    receiveShadow
    position={[0, -0.5, -1]}
    rotation={[Math.PI / 2, -rotation, 0]}
  >
    <T.CylinderGeometry args={[0.09, 0.09, 1, geometrySegments]} />
    <T.MeshStandardMaterial color="black" />
  </T.Mesh>
  {#if !isLowEndDevice}
    <Model position={[0, -0.5, -1]} rotation={[Math.PI / 2, -rotation, 0]} />
  {/if}
  <T.Mesh
    receiveShadow
    position={[0.7, -0.5, -1]}
    rotation={[Math.PI / 2, -rotation, 0]}
  >
    <T.CylinderGeometry args={[0.09, 0.09, 1, 12]} />
    <T.MeshStandardMaterial color="black" />
  </T.Mesh>
  <Model position={[0.7, -0.5, -1]} rotation={[Math.PI / 2, rotation, 0]} />

  {#if !isMobile}
    <T.Mesh receiveShadow position={[0, 0 + 4 * Math.sin(rotation) - 10, 10]}>
      <T.CylinderGeometry args={[2, 2, 10, geometrySegments]} />
      <T.MeshStandardMaterial color="darkblue" />
    </T.Mesh>
    <T.Mesh receiveShadow position={[-3, 0 + 4 * Math.cos(rotation) - 10, 10]}>
      <T.CylinderGeometry args={[2, 2, 10, geometrySegments]} />
      <T.MeshStandardMaterial color="darkblue" />
    </T.Mesh>
    <T.Mesh receiveShadow position={[-1, 0 + Math.cos(rotation), -1]}>
      <T.CylinderGeometry args={[0.2, 0.2, 1, 15]} />
      <T.MeshStandardMaterial color="darkblue" />
    </T.Mesh>
  {/if}
  <T.Mesh receiveShadow position={[-1, 0 + Math.sin(rotation), -2]}>
    <T.CylinderGeometry args={[0.2, 0.2, 1, 15]} />
    <T.MeshStandardMaterial color="darkblue" />
  </T.Mesh>
  <T.Mesh receiveShadow position={[1, 0 - Math.cos(rotation * 2), -2]}>
    <T.CylinderGeometry args={[0.2, 0.2, 0.9, 15]} />
    <T.MeshStandardMaterial color="darkblue" />
  </T.Mesh>
  <T.Mesh receiveShadow position={[0, 0 - Math.sin(rotation), -2]}>
    <T.CylinderGeometry args={[0.2, 0.2, 0.9, 15]} />
    <T.MeshStandardMaterial color="darkblue" />
  </T.Mesh>

  <Box
    position={[-1, 0, -1]}
    color="black"
    lights={isMobile ? [] : [{ position: [1, 1, -1], intensity: 15 }]}
  />
  <Box
    position={[0, 0, -2]}
    color="black"
    geometry={[3.4, 1, 1]}
    lights={isMobile ? [] : [{ position: [1, 1, 2], intensity: 5 }]}
  />
  <Box
    position={[8, -10, 3]}
    color="black"
    geometry={[2, 12, 2]}
    lights={isMobile ? [] : [{ position: [1, 2, 1], intensity: 5 }]}
  />
  <Box
    position={[-32, -9, 32]}
    color="black"
    geometry={[2, 8, 5]}
    lights={isMobile ? [] : [{ position: [3, 2, 2], intensity: 5 }]}
  />

  {#if !isMobile}
    <Box
      position={[22, -4, -3.9]}
      color="black"
      geometry={[0.2, 6, 6]}
      lights={[{ position: [2, 2, 2], intensity: 5 }]}
    />
    <Box
      position={[-5, 8, 9]}
      color="black"
      geometry={[0.2, 11, 9]}
      lights={[{ position: [2, 4.5, 4], intensity: 2 }]}
    />
    <Box
      position={[-5, 12, -19]}
      color="black"
      geometry={[0.2, 11, 19]}
      lights={[{ position: [3, 4.5, 7], intensity: 2 }]}
    />
  {/if}
  {#if !isMobile}
    <Gear
      position={[0, 10, 0]}
      rotation={[0, 0, 0]}
      size={[2, 2, 2]}
      isActive={true}
      rotationSpeed={4}
    />
    <Gear
      position={[1, 10, -3.7]}
      rotation={[0, 0, 0]}
      size={[8, 8, 8]}
      isActive={true}
      rotationSpeed={-1}
    />
    <Gear
      position={[4.5, 10, 14]}
      rotation={[0, 0, 0]}
      size={[6, 6, 6]}
      isActive={true}
      rotationSpeed={5}
    />
    <Gear
      position={[2, 3, 9]}
      rotation={[0, 0, 0]}
      size={[13, 13, 13]}
      isActive={true}
      rotationSpeed={-5}
    />
  {/if}
  <Gear
    position={[-4, 6, -10]}
    rotation={[Math.PI / 2, 0, 0]}
    size={[16, 16, 16]}
    isActive={true}
    rotationSpeed={0.5}
  />
  <T.PointLight position={[10, 5,10 ]} intensity={25} color="purple" />
  <Gear
    position={[-10, 12, 4]}
    rotation={[0, 0, Math.PI / 2]}
    orientation={0}
    size={[38, 38, 38]}
    isActive={true}
    rotationSpeed={-0.1}
  />
  <Gear
    position={[9, 1, 1]}
    rotation={[Math.PI / 4, 0, Math.PI / 2]}
    orientation={0}
    size={[48, 48, 48]}
    isActive={true}
    rotationSpeed={-0.03}
  />

  <T.Mesh receiveShadow position={[2, 0, 9]}>
    <T.CylinderGeometry args={[1.1, 1.1, 100, 15]} />
    <T.MeshPhysicalMaterial color="black" />
  </T.Mesh>
  <T.Mesh receiveShadow position={[1, 30, -3.7]}>
    <T.CylinderGeometry args={[0.6, 0.6, 40, 15]} />
    <T.MeshPhysicalMaterial color="black" />
  </T.Mesh>
  <Nucleus {isMobile} />
  <FloorGrid />
</Suspense>
