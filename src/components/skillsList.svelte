<script lang="ts">
  import SectionJump from "./common/sectionJump.svelte";
  import Azure from "./skills-logos/azure.svelte";
  import React from "./skills-logos/react_light.svelte";
  import Express from "./skills-logos/expressjs.svelte";
  import Node from "./skills-logos/nodejs.svelte";
  import JavaScript from "./skills-logos/javascript.svelte";
  import HTML from "./skills-logos/html5.svelte";
  import CSS from "./skills-logos/css.svelte";
  import AWS from "./skills-logos/aws.svelte";
  import PostgreSQL from "./skills-logos/postgresql.svelte";
  import Flutter from "./skills-logos/flutter.svelte";
  import Firebase from "./skills-logos/firebase.svelte";
  import Python from "./skills-logos/python.svelte";
  import Cypress from "./skills-logos/cypress.svelte";
  import Svelte from "./skills-logos/svelte.svelte";
  import Docker from "./skills-logos/docker.svelte";
  import MongoDB from "./skills-logos/mongodb.svelte";
  import ThreeJS from "./skills-logos/threejs.svelte";
  import TypeScript from "./skills-logos/typescript.svelte";
  interface Skill {
    name: string;
    component: any;
  }

  let mainSkills: Skill[] = [
    {
      name: "React",
      component: React,
    },
    {
      name: "Express",
      component: Express,
    },
    {
      name: "AWS",
      component: AWS,
    },
    {
      name: "Node",
      component: Node,
    },
    {
      name: "JavaScript",
      component: JavaScript
    },
    {
      name: "HTML",
      component: HTML,
    },
    {
      name: "CSS",
      component: CSS,
    },    
    {
      name: "PostgreSQL",
      component: PostgreSQL,
    },
    {
      name: "Flutter",
      component: Flutter,
    },
    {
      name: "Firebase",
      component: Firebase,
    }
  ];

  let secondarySkills: Skill[] = [
    {
      name: "TypeScript",
      component: TypeScript
    },
    {
      name: "ThreeJS",
      component: ThreeJS
    },
    {
      name: "Python",
      component: Python
    },
    {
      name: "Azure",
      component: Azure
    },
    {
      name: "Cypress",
      component: Cypress
    },
    {
      name: "Svelte",
      component: Svelte
    },
    {
      name: "Docker",
      component: Docker
    },
    {
      name: "MongoDB",
      component: MongoDB
    }
  ];
</script>

<main>
  <section id="skills">
    <h2>My main Skills</h2>
    <div class="row">
      {#each mainSkills as skill}
        <div class="skill-item">
          <svelte:component this={skill.component}/>
          <h3>{skill.name}</h3>
        </div>
      {/each}
    </div>
    <h2>I also know about</h2>
    <div class="row">
      {#each secondarySkills as skill}
        <div class="skill-item">          
          <svelte:component this={skill.component}/>
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
      opacity: 0.4;
      transform: translateX(-100px);
    }
    100% {
      opacity: 1;
      transform: translateX(0);
    }
  }

  section {
    margin-bottom: 200px;
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
  .row {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
    justify-items: center;
    padding: 0 20px;
  }
  @media (max-width: 768px) {
    .row {
      grid-template-columns: 1fr;
    }
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
