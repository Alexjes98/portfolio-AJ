<script>
  import * as Threlte from "@threlte/core";
  import * as Three from "three";

  import { T, useTask } from "@threlte/core";
  import { AmbientLight, GridHelper, Vector3 } from "three";
  import { OrbitControls } from "@threlte/extras";
  import { onMount } from "svelte";
  import { Grid, interactivity, Environment, GLTF } from "@threlte/extras";
  import { spring } from "svelte/motion";
  import Box from "./components/Box.svelte";
  import Gear from "./components/Gear.svelte";
  interactivity();

  let rotation = 0;
  useTask((delta) => {
    rotation += delta;
  });

  class FallingSphere {
    /**
     * @param {any} args
     * @param {any} position
     * @param {any} rotation
     * @param {number} initialPos
     * @param {number} speed
     */
    constructor(args, position, rotation, initialPos, speed) {
      this.args = args;
      this.position = position;
      this.rotation = rotation;
      this.initialPos = initialPos;
      this.speed = speed;
    }
  }

  useTask((delta) => {
    for (let i = 0; i < fallingCubes.length; i++) {
      if (fallingCubes[i]) {
        if (fallingCubes[i]) {
          fallingCubes[i].position[0] += delta * fallingCubes[i].speed;
          fallingCubes[i].position[1] = (4 * Math.sin(
            delta * fallingCubes[i].position[0]
          ));
        }
      }
      if (fallingCubes[i].position[0] > 800) {
        fallingCubes[i].position[0] = fallingCubes[i].initialPos;
      }
    }
  });
  const values = [
    //initial pos is x
    {
      args: [0.2, 5],
      position: [-80, 0, -4],
      rotation: [0, 0.1, 0],
      initialPos: -80,
      speed: 19,
    },
    {
      args: [0.1, 22],
      position: [-150, -2, 2],
      rotation: [0, 0.1, 0],
      initialPos: -150,
      speed: 22,
    },
    {
      args: [0.2, 22],
      position: [-66, 0, -2],
      rotation: [0, 0.1, 0],
      initialPos: -66,
      speed: 43,
    },
    {
      args: [0.1, 22],
      position: [-190, -4, -2],
      rotation: [0, 0.1, 0],
      initialPos: -190,
      speed: 18,
    },
    {
      args: [0.2, 11],
      position: [-60, 0, 1],
      rotation: [0, 0.1, 0],
      initialPos: -60,
      speed: 16,
    },
    {
      args: [0.1, 22],
      position: [-160, -3, -5],
      rotation: [0, 0.1, 0],
      initialPos: -160,
      speed: 23,
    },
    {
      args: [0.1, 22],
      position: [-260, 0, 10],
      rotation: [0, 0.1, 0],
      initialPos: -260,
      speed: 73,
    },
    {
      args: [0.2, 22],
      position: [-360, -4, 10],
      rotation: [0, 0.1, 0],
      initialPos: -360,
      speed: 90,
    },
    {
      args: [0.1, 22],
      position: [-260, -4, -10],
      rotation: [0, 0.1, 0],
      initialPos: -260,
      speed: 90,
    },
    {
      args: [0.2, 22],
      position: [-260, -7, 0],
      rotation: [0, 0.1, 0],
      initialPos: -260,
      speed: 90,
    },
    {
      args: [0.1, 22],
      position: [-560, -7, 38],
      rotation: [0, 0.1, 0],
      initialPos: -560,
      speed: 80,
    },
    {
      args: [0.2, 22],
      position: [-560, 0, -25],
      rotation: [0, 0.1, 0],
      initialPos: -560,
      speed: 100,
    },
    {
      args: [0.2, 22],
      position: [-560, 0, -45],
      rotation: [0, 0.1, 0],
      initialPos: -560,
      speed: 120,
    },
    {
      args: [0.2, 22],
      position: [-260, -4, 65],
      rotation: [0, 0.1, 0],
      initialPos: -260,
      speed: 80,
    },
    {
      args: [0.1, 22],
      position: [-660, -14, -65],
      rotation: [0, 0.1, 0],
      initialPos: -660,
      speed: 120,
    },
    {
      args: [0.1, 22],
      position: [-560, -24, 13],
      rotation: [0, 0.1, 0],
      initialPos: -560,
      speed: 120,
    },
    {
      args: [0.1, 22],
      position: [-560, -36, -13],
      rotation: [0, 0.1, 0],
      initialPos: -560,
      speed: 100,
    },
    {
      args: [0.1, 22],
      position: [-400, -10, -13],
      rotation: [0, 0.1, 0],
      initialPos: -400,
      speed: 300,
    },
    {
      args: [0.1, 22],
      position: [-320, -10, 33],
      rotation: [0, 0.1, 0],
      initialPos: -320,
      speed: 100,
    },
  ];
  const fallingCubes = values.map(
    (value) =>
      new FallingSphere(
        value.args,
        value.position,
        value.rotation,
        value.initialPos,
        value.speed
      )
  );

  let cameraPosition = [0, 0, 0];

  let scrollY = 0;

  $: {
    if (scrollY < 2000) {
      cameraPosition = cameraPosition.map((v, i) => {
        return scrollY / 100;
      });
    } else if (scrollY < 4000) {
      cameraPosition = [0 + scrollY / 100, 0, 0];
    } else if (scrollY < 9000) {
      cameraPosition = [-5, -40 + scrollY / 100, 0];
    } else {
      cameraPosition = [0 + scrollY / 100, 0, 0];
    }
  }

  // function onWindowResize() {
  //   camera.aspect = window.innerWidth / window.innerHeight;
  //   camera.updateProjectionMatrix();

  //   renderer.setSize(window.innerWidth, window.innerHeight);
  // }

  $: console.log(scrollY);
  $: console.log(cameraPosition);
</script>

<svelte:window bind:scrollY />

<T.PerspectiveCamera
  makeDefault
  position={cameraPosition}
  on:create={({ ref }) => {
    ref.lookAt(0, 0, 0);
  }}
>
  <OrbitControls enableDamping target={[0, 0, 0]} />
</T.PerspectiveCamera>

<!-- <T.DirectionalLight position={[20, 40, 20]} castShadow intensity={10} /> -->

<!-- <T.GridHelper args={[100, 100]} /> -->

<Box
  position={[-1, 0, -1]}
  color="black"
  lights={[{ position: [1, 1, -1], intensity: 15 }]}
/>
<Box
  position={[0, 0, -2]}
  color="black"
  geometry={[3.4, 1, 1]}
  lights={[{ position: [1, 1, 2], intensity: 20 }]}
/>
<Box
  position={[8, -10, 3]}
  color="black"
  geometry={[2, 12, 2]}
  lights={[{ position: [1, 2, 1], intensity: 25 }]}
/>
<Box
  position={[-32, -3, -20]}
  color="black"
  geometry={[2, 2, 5]}
  lights={[{ position: [1, 2, 1], intensity: 25 }]}
/>
<Box
  position={[-32, -9, 32]}
  color="black"
  geometry={[2, 8, 5]}
  lights={[{ position: [3, 2, 2], intensity: 25 }]}
/>
<Box
  position={[22, -4, -3.9]}
  color="black"
  geometry={[0.2, 6, 6]}
  lights={[{ position: [2, 2, 2], intensity: 25 }]}
/>
<Box
  position={[-5, 8, 9]}
  color="black"
  geometry={[0.2, 11, 9]}
  lights={[{ position: [2, 4.5, 4], intensity: 105 }]}
/>
<Box
  position={[-5, 12, -19]}
  color="black"
  geometry={[0.2, 11, 19]}
  lights={[{ position: [3, 4.5, 7], intensity: 200 }]}
/>
<Gear
  position={[0, 10, 0]}
  rotation={[0, 0, 0]}
  geometry={[2, 2, 1, 8]}
  lights={[]}
  isActive={true}
  rotationSpeed={2}
/>
<Gear
  position={[1, 10, -3.7]}
  rotation={[0, 0, 0]}
  geometry={[2, 2, 1, 8]}
  lights={[]}
  isActive={true}
  rotationSpeed={-2}
/>
<Gear
  position={[-8, 8, -3.7]}
  rotation={[0, 0, 0]}
  geometry={[5, 5, 1, 10]}
  lights={[]}
  isActive={true}
  rotationSpeed={-2}
/>
<Gear
  position={[2, 3, 9]}
  rotation={[0, 0, 0]}
  geometry={[3, 3, 2, 9]}
  lights={[]}
  isActive={true}
  rotationSpeed={-2}
/>
<Gear
  position={[2, 6, 7]}
  rotation={[0, 0, 0]}
  geometry={[3, 3, 2, 9]}
  lights={[]}
  isActive={true}
  rotationSpeed={2}
/>
<Gear
  position={[2, 9, 4]}
  rotation={[0, 0, 0]}
  geometry={[3, 3, 2, 9]}
  lights={[]}
  isActive={true}
  rotationSpeed={-2}
/>

<T.Mesh receiveShadow position={[0, -60, 0]}>
  <T.BoxGeometry args={[800, 0, 800]} />
  <T.MeshStandardMaterial color="white" />
</T.Mesh>
<T.Mesh receiveShadow position={[0, 20, -140]}>
  <T.BoxGeometry args={[800, 200, 1]} />
  <T.MeshStandardMaterial color="white" />
</T.Mesh>
<T.Mesh receiveShadow position={[0, 0, 60]}>
  <T.BoxGeometry args={[800, 200, 10]} />
  <T.MeshStandardMaterial color="white" />
</T.Mesh>
<T.Mesh receiveShadow position={[-300, 0, 0]}>
  <T.BoxGeometry args={[10, 400, 400]} />
  <T.MeshStandardMaterial color="white" />
</T.Mesh>
<T.Mesh receiveShadow position={[800, 0, 0]}>
  <T.BoxGeometry args={[10, 400, 600]} />
  <T.MeshStandardMaterial color="white" />
</T.Mesh>
<T.Mesh receiveShadow position={[0, 80, 0]}>
  <T.BoxGeometry args={[800, 10, 800]} />
  <T.MeshStandardMaterial color="white" />
</T.Mesh>

{#each fallingCubes as cube}
  <T.Mesh
    position={[cube.position[0], cube.position[1], cube.position[2]]}
    rotation.y={rotation}
  >
    <T.PointLight position={[0, 0, 0]} intensity={500} color="blue" />
    <T.SphereGeometry args={cube.args} />
    <T.MeshBasicMaterial color="blue" />
  </T.Mesh>
{/each}

<!-- Home Page
 //A brief introduction about yourself
A headshot or logo
//A tagline that summarizes your expertise
About Page
Your professional background
Your skills and areas of expertise
Personal interests or hobbies that relate to your profession
Portfolio/Gallery
High-quality images or screenshots of your work
Descriptions of each project, including your role and the tools used
Case studies or success stories
Resume/CV
A downloadable PDF of your resume
A detailed list of your work experience, education, and certifications
Services Page (if applicable)
The services you offer
Pricing or rate information
Testimonials from clients or colleagues
Blog/Articles
Original articles or blog posts related to your field
Tutorials or how-to guides
Industry insights or commentary
Contact Information
An email address or contact form
Links to your professional social media profiles
A call-to-action encouraging visitors to get in touch
Extras
Press mentions or awards
A calendar of events or workshops
A portfolio of personal projects or hobbies -->
