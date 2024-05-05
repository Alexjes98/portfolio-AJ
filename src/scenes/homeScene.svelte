<script>
  import { T, useTask } from "@threlte/core";
  import { AmbientLight, GridHelper } from "three";
  import { OrbitControls } from "@threlte/extras";
  import { onMount } from "svelte";

  let rotation = 0;
  useTask((delta) => {
    rotation += delta;
  });

  useTask((delta) => {});

  let cameraPosition = [2, 2, 7];
  // @ts-ignore
  useTask((delta) => {
    console.log(scrollY);
    if (scrollY < 1200) {
      cameraPosition[0] = 20 + scrollY / 100;
      cameraPosition[1] = scrollY / 100;
      cameraPosition[2] = scrollY / 100;
    } else {
      cameraPosition[0] = scrollY / 100;
      cameraPosition[1] = scrollY / 100;
      cameraPosition[2] = scrollY / 100;
    }
  });

  let scrollY = 0;
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
<T.AmbientLight intensity={0.5} />
<T.DirectionalLight position={[0, 10, 0]} intensity={1} />

<T.GridHelper args={[100, 100]} />

<T.Mesh position={[20, 8, 6]} rotation.y={rotation}>
  <T.BoxGeometry args={[7, 7, 7]} />
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
