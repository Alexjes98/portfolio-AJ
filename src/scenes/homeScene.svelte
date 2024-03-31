<script>
  import { T, useTask } from "@threlte/core";
  import { AmbientLight, GridHelper } from "three";
  import { OrbitControls } from "@threlte/extras";



  let rotation = 0;
  useTask((delta) => {
    rotation += delta;
    console.log(rotation);
  });

  
  useTask((delta) => {
    for (let i = 0; i < fallingCubes.length; i++) {
      fallingCubes[i].position[1] -= delta;
      if (fallingCubes[i].position[1] < 0) {
        fallingCubes[i].position[1] = fallingCubes[i].initialHeight;
      }
    }
    
  });
  const fallingCubes = [
    { args: [1,0.5,0.5], position: [-0.4, 5 , 5], rotation: [0, 0.1, 0], initialHeight: 5 }, // cube 0
    { args: [1,0.5,0.5], position: [0.3, 2, 5], rotation: [0, 0.1, 0], initialHeight: 7 }, // cube 1
    { args: [1,0.5,0.5], position: [1, 6, 5], rotation: [0, 0.1, 0], initialHeight: 6 }, // cube 2
    { args: [1,0.5,0.5], position: [1.7, 6.5, 5], rotation: [0, 0.1, 0], initialHeight: 6.5 }, // cube 3
    { args: [1,0.5,0.5], position: [2.4, 4.6, 5], rotation: [0, 0.1, 0], initialHeight: 4.6 }, // cube 4
    { args: [1,0.5,0.5], position: [3.1, 4.5, 5], rotation: [0, 0.1, 0], initialHeight: 4.5 }, // cube 5
    { args: [1,0.5,0.5], position: [3.8, 4.9, 5], rotation: [0, 0.1, 0], initialHeight: 4.9 }, // cube 6
    { args: [1,0.5,0.5], position: [4.5, 5.9, 5], rotation: [0, 0.1, 0], initialHeight: 5.9 }, // cube 7
    { args: [1,0.5,0.5], position: [5.2, 6.2, 5], rotation: [0, 0.1, 0], initialHeight: 6.2 }, // cube 8
    { args: [1,0.5,0.5], position: [5.9, 5.4, 5], rotation: [0, 0.1, 0], initialHeight: 5.4 }, // cube 9
  ];
</script>

<T.PerspectiveCamera
  makeDefault
  position={[2, 3, 7]}
  on:create={({ ref }) => {
    ref.lookAt(0, 0, 0);
  }}
>
  <OrbitControls enableDamping target={[0, 0, 0]} />
</T.PerspectiveCamera>
<T.AmbientLight intensity={0.5} />
<T.DirectionalLight position={[0, 10, 0]} intensity={1} />

<T.GridHelper args={[100, 100]} />
{#each fallingCubes as cube}
  <T.Mesh position={[cube.position[0],cube.position[1],cube.position[2]]} rotation={cube.rotation}>
    <T.BoxGeometry args={cube.args} />
    <T.MeshBasicMaterial color="#222831" />
  </T.Mesh>
{/each}

<T.Mesh position.y={1} rotation.y={rotation}>
  <T.BoxGeometry args={[1, 1, 1]} />
  <T.MeshBasicMaterial color="black" />
</T.Mesh>

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
