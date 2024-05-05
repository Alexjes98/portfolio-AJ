<script>
  let mainSkills = [
    {
      name: "Node",
      img: "https://raw.githubusercontent.com/devicons/devicon/master/icons/nodejs/nodejs-original-wordmark.svg",
    },
    {
      name: "Express",
      img: "https://raw.githubusercontent.com/devicons/devicon/master/icons/express/express-original-wordmark.svg",
    },
    {
      name: "React",
      img: "https://camo.githubusercontent.com/d764e0d1b0bb6fc6e65157b3c98b9e203a13a17390309fad633406c3324dbfb2/68747470733a2f2f72656163746e61746976652e6465762f696d672f6865616465725f6c6f676f2e737667",
    },
    {
      name: "JavaScript",
      img: "https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg",
    },
    {
      name: "HTML",
      img: "https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original-wordmark.svg",
    },
    {
      name: "CSS",
      img: "https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original-wordmark.svg",
    },
    {
      name: "AWS",
      img: "https://raw.githubusercontent.com/devicons/devicon/master/icons/amazonwebservices/amazonwebservices-original-wordmark.svg",
    },
    {
      name: "Azure",
      img: "https://raw.githubusercontent.com/devicons/devicon/master/icons/azure/azure-original-wordmark.svg",
    },
    
    {
      name: "PostgreSQL",
      img: "https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original-wordmark.svg",
    },
    {
      name: "Flutter",
      img: "https://camo.githubusercontent.com/a682e207ce9939518c8617c6340b1bf8b1769b30a9f1b45d27d67fd64af1d0f2/68747470733a2f2f7777772e766563746f726c6f676f2e7a6f6e652f6c6f676f732f666c7574746572696f2f666c7574746572696f2d69636f6e2e737667",
    },
    {
      name: "Firebase",
      img: "https://camo.githubusercontent.com/3e5344a2965e786497ceb575ad67d2c64d412bb9683da05791edf424a0e40734/68747470733a2f2f7777772e766563746f726c6f676f2e7a6f6e652f6c6f676f732f66697265626173652f66697265626173652d69636f6e2e737667",
    },
    {
      name: "Cypress",
      img: "https://www.cypress.io/_astro/navbar-brand.D87396b0.svg",
    },
  ];

  let secondarySkills = [
    {
      name: "Python",
      img: "https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original-wordmark.svg",
    },    
    {
      name: "Svelte",
      img: "https://raw.githubusercontent.com/devicons/devicon/master/icons/svelte/svelte-original-wordmark.svg",
    },    
    {
      name: "Docker",
      img: "https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original-wordmark.svg",
    },
    {
      name: "MongoDB",
      img: "https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original-wordmark.svg",
    },
  ];
</script>

<main>
  <section>
    <h2>My main Skills</h2>
    <div class="row">
      {#each mainSkills as skill}
        <div class="skill-item">
          <img src={`${skill.img}`} alt={skill.name} />
          <h3>{skill.name}</h3>
        </div>
      {/each}
    </div>
    <h2>I also know about</h2>
    <div class="row">
      {#each secondarySkills as skill}
        <div class="skill-item
        ">
          <img src={`${skill.img
          }`} alt={skill.name} />
          <h3>{skill.name}</h3>
        </div>
      {/each}
    </div>
  </section>
</main>

<style>
  section {
    margin-bottom: 300px;
    padding: 20px;
  }
  .skill-item {
    width: 200px;
    margin: 50px;
    padding: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  img {
    width: 100px;
    height: 100px;
  }
  .row {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    background-color: var(--accent-color);
  }
</style>
