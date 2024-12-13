<script>
  import SectionJump from "./common/sectionJump.svelte";

  let mainSkills = [
    {
      name: "React",
      img: "/reactskill.png",
    },
    {
      name: "Express",
      img: "https://raw.githubusercontent.com/devicons/devicon/master/icons/express/express-original-wordmark.svg",
    },
    {
      name: "Node",
      img: "https://raw.githubusercontent.com/devicons/devicon/master/icons/nodejs/nodejs-original-wordmark.svg",
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
      name: "PostgreSQL",
      img: "https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original-wordmark.svg",
    },
    {
      name: "Flutter",
      img: "/flutter.png",
    },
    {
      name: "Firebase",
      img: "/firebase.png",
    },
  ];

  let secondarySkills = [
    {
      name: "Python",
      img: "https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original-wordmark.svg",
    },
    {
      name: "Azure",
      img: "https://raw.githubusercontent.com/devicons/devicon/master/icons/azure/azure-original-wordmark.svg",
    },
    {
      name: "Cypress",
      img: "https://www.cypress.io/_astro/navbar-brand.D87396b0.svg",
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
  <section id="skills">
    <h2>My main Skills</h2>
    <div class="row">
      {#each mainSkills as skill}
        <div class="skill-item">
          <img src={`${skill.img}`} alt={skill.name} loading="lazy"  />
          <h3>{skill.name}</h3>
        </div>
      {/each}
    </div>
    <h2>I also know about</h2>
    <div class="row">
      {#each secondarySkills as skill}
        <div
          class="skill-item
        "
        >
          <img src={`${skill.img}`} alt={skill.name} loading="lazy" />
          <h3>{skill.name}</h3>
        </div>
      {/each}
    </div>
    <SectionJump href="#contact" />
  </section>
</main>

<style>
  @keyframes fade-in-left {
    0% {
      opacity: 0;
      transform: translateX(-600px);
    }
    100% {
      opacity: 1;
      transform: translateX(0);
    }
  }

  section {
    margin-bottom: 8000px;
    padding: 20px;
  }
  @media (prefers-reduced-motion: no-preference) {
    @supports (animation-timeline: scroll()) {
      .skill-item {
        animation: fade-in-left 0.5s ease;
        animation-timeline: view();
      }
    }
  }
  .skill-item {    
    width: 200px;
    margin: 30px;
    padding: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: var(--main-color);
    border-radius: 10px;
  }
  img {
    width: 100px;
    height: 100px;
  }
  .row {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  }
  h2 {
    font-size: 2em;
    font-weight: bold;
    text-align: center;
    color: white;
    margin-bottom: 35px;
    width: 100%;
    font-family: "Courier New", Courier, monospace;
    font-weight: bold;
    text-align: center;
  }
</style>
