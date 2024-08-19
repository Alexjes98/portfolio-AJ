<script>
  // @ts-nocheck

  import * as Threlte from "@threlte/core";
  import * as Three from "three";

  import Model from "../../gear.svelte";

  import { T, useTask } from "@threlte/core";
  import { AmbientLight, GridHelper, Vector3, DoubleSide } from "three";
  import { OrbitControls, useGltf } from "@threlte/extras";
  import { onMount } from "svelte";
  import {
    Grid,
    interactivity,
    Environment,
    GLTF,
    ImageMaterial,
  } from "@threlte/extras";
  import { spring } from "svelte/motion";
  import Box from "./components/Box.svelte";
  import ProjectItem from "./components/ProjectItem.svelte";
  import Gear from "./components/Gear.svelte";

  import { PI } from "three/examples/jsm/nodes/Nodes.js";
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
          fallingCubes[i].position[1] =
            4 * Math.sin(delta * fallingCubes[i].position[0]);
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
  let isMobile = window.innerWidth < 768;

  $: {
    if (isMobile) {
      if (scrollY < 2000) {
        cameraPosition = cameraPosition.map((v, i) => {
          return scrollY / 100;
        });
      } else if (scrollY < 7000) {
        cameraPosition = [-12 + 0 + scrollY / 100, 0, 0];
      } else if (scrollY < 13000) {
        cameraPosition = [-5, -70 + scrollY / 100, 0];
      } else if (scrollY < 24000) {
        cameraPosition = [-20 + scrollY / 100, 0, 5+ 100 - scrollY / 100];
      } else {
        cameraPosition = [-300 + scrollY / 100, 0, +60];
      }
    } else {
      if (scrollY < 2000) {
        cameraPosition = cameraPosition.map((v, i) => {
          return scrollY / 100;
        });
      } else if (scrollY < 6000) {
        cameraPosition = [-12 + 0 + scrollY / 100, 0, 0];
      } else if (scrollY < 11000) {
        cameraPosition = [-5, -60 + scrollY / 100, 0];
      } else if (scrollY < 22000) {
        cameraPosition = [-30 + scrollY / 100, 0, 100 - scrollY / 100];
      } else {
        cameraPosition = [-300 + scrollY / 100, 0, +60];
      }
    }
  }

  // function onWindowResize() {
  //   camera.aspect = window.innerWidth / window.innerHeight;
  //   camera.updateProjectionMatrix();

  //   renderer.setSize(window.innerWidth, window.innerHeight);
  // }

  $: console.log(scrollY);
</script>

<svelte:window bind:scrollY />

<T.PerspectiveCamera
  makeDefault
  position={cameraPosition}
  aspect={window.innerWidth / window.innerHeight}
  on:create={({ ref }) => {
    ref.lookAt(0, 0, 0);
  }}
>
  <OrbitControls enableDamping target={[0, 0, 0]} />
</T.PerspectiveCamera>

<T.DirectionalLight position={[0, 10, 0]} castShadow intensity={10} />

<!-- <T.GridHelper args={[100, 100]} /> -->

<Model position={[0, -0.5, -1]} rotation={[Math.PI / 2, -rotation, 0]} />
<Model position={[0.7, -0.5, -1]} rotation={[Math.PI / 2, rotation, 0]} />

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
  size={[2, 2, 2]}
  lights={[]}
  isActive={true}
  rotationSpeed={4}
/>
<Gear
  position={[1, 10, -3.7]}
  rotation={[0, 0, 0]}
  size={[8, 8, 8]}
  lights={[]}
  isActive={true}
  rotationSpeed={-1}
/>
<Gear
  position={[4.5, 10, 14]}
  rotation={[0, 0, 0]}
  size={[6, 6, 6]}
  lights={[]}
  isActive={true}
  rotationSpeed={5}
/>
<Gear
  position={[2, 3, 9]}
  rotation={[0, 0, 0]}
  size={[13, 13, 13]}
  lights={[]}
  isActive={true}
  rotationSpeed={-5}
/>
<Gear
  position={[-4, 6, -10]}
  rotation={[Math.PI / 2, 0, 0]}
  size={[16, 16, 16]}
  lights={[]}
  isActive={true}
  rotationSpeed={0.5}
/>
<Gear
  position={[-10, 12, 4]}
  rotation={[0, 0, Math.PI / 2]}
  orientation={0}
  size={[38, 38, 38]}
  lights={[]}
  isActive={true}
  rotationSpeed={-0.1}
/>
<Gear
  position={[9, 1, 1]}
  rotation={[Math.PI / 4, 0, Math.PI / 2]}
  orientation={0}
  size={[48, 48, 48]}
  lights={[]}
  isActive={true}
  rotationSpeed={-0.03}
/>

<T.Mesh receiveShadow position={[2, 0, 9]}>
  <T.CylinderGeometry args={[1.1, 1.1, 100, 15]} />
  <T.MeshStandardMaterial color="black" />
</T.Mesh>
<T.Mesh receiveShadow position={[1, 30, -3.7]}>
  <T.CylinderGeometry args={[0.6, 0.6, 40, 15]} />
  <T.MeshStandardMaterial color="black" />
</T.Mesh>

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

<ProjectItem
  position={[75, 0, -20]}
  rotation={[0, Math.PI - 3 / 2, 0]}
  geometry={[20, 11.5, 1]}
  url="stipe.png"
  items={[
    { url: "react.png" },
    { url: "ec2.jpeg" },
    { url: "nodejs.png" },
    { url: "amplify.jpeg" },
  ]}
/>

<ProjectItem
  position={[95, 0, -40]}
  rotation={[0, Math.PI - 3 / 2, 0]}
  geometry={[23, 11.3, 1]}
  url="littlebellies.png"
  items={[
    { url: "react.png" },
    { url: "cy.jpeg" },
    { url: "lambda.png" },
    { url: "dinamo.png" },
  ]}
/>

<ProjectItem
  position={[115, 0, -60]}
  rotation={[0, Math.PI - 3 / 2, 0]}
  geometry={[23, 11.5, 1]}
  url="progressive.png"
  items={[
    { url: "remix.jpg", zoom: 0.7 },
    { url: "beanstalk.jpeg" },
    { url: "cy.jpeg" },
    { url: "nodejs.png" },
    { url: "postgres.png" },
    { url: "cognito.png" },
    { url: "s3.jpeg" },
  ]}
/>

<ProjectItem
  position={[138, 0, -80]}
  rotation={[0, Math.PI - 3 / 2, 0]}
  geometry={[20, 11.5, 1]}
  url="skynet.png"
  items={[
    { url: "react.png" },
    { url: "amplify.jpeg" },
    { url: "cy.jpeg" },
    { url: "nodejs.png" },
    { url: "postgres.png" },
    { url: "cognito.png" },
    { url: "s3.jpeg" },
  ]}
/>

<ProjectItem
  position={[158, 0, -100]}
  rotation={[0, Math.PI - 3 / 2, 0]}
  geometry={[20, 11.5, 1]}
  url="clew.png"
  items={[
    { url: "azure.png" },
    { url: "react.png" },
    { url: "python.jpg" },
    { url: "function.png" },
    { url: "search.png" },
    { url: "openai.png" },
    { url: "cosmosdb.jpg" },
  ]}
/>

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
