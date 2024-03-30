<script>
  import { T, useTask } from "@threlte/core";
  import { AmbientLight, GridHelper } from "three";
  import { OrbitControls } from '@threlte/extras'
  let rotation = 0;
  useTask((delta) => {
    rotation += delta;
  });
</script>

<T.PerspectiveCamera
  makeDefault
  position={[5, 3, 5]}
  on:create={({ ref }) => {
    ref.lookAt(0, 1, 0);
  }}
>
<OrbitControls
    enableDamping
    target={[0, 0, 0]}
  />
</T.PerspectiveCamera>
<T.AmbientLight intensity={0.5} />
<T.DirectionalLight position={[0, 10, 0]} intensity={1} />

<T.GridHelper args={[100, 100]} />

<T.Mesh 
position.y={1}
rotation.y={rotation}>
  <T.BoxGeometry args={[2, 2, 1]} />
  <T.MeshBasicMaterial color="black" />
</T.Mesh>

<!-- Home Page
A brief introduction about yourself
A headshot or logo
A tagline that summarizes your expertise
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