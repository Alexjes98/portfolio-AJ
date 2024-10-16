<script>
  import SectionJump from "./common/sectionJump.svelte";

  let education = [
    {
      date: "2016-2023",
      location: "Táchira, Venezuela",
      title: "Informatic Engineering",
      institution: "Experimental National University of Táchira (UNET)",
    },
    {
      date: "2022-2022",
      location: "Táchira, Venezuela",
      title: "AWS Certified Cloud Practitioner",
      institution: "AWS Training and Certification",
    },
    {
      date: "2024-2024",
      location: "Táchira, Venezuela",
      title: "AWS Certified AI Practitioner",
      institution: "AWS Training and Certification",
    },
  ];

  let experience = [
    {
      date: "2022-2024",
      location: "Bógota, Colombia (Remote)",
      title: "Fullstack Developer",
      institution: "Hamal Solutions",
    },
    {
      date: "2020-2023",
      location: "Guatemala City, Guatemala (Remote)",
      title: "Fullstack/Mobile Developer",
      institution: "Stipe",
    },
  ];
</script>

<main>
  <section id="journey-resume">
    <div class="journey-container">
      <div class="col">
        <div>
          <h2>Experience</h2>
        </div>
        {#each experience as item}
          <div class="experience-item">
            <p>{item.date}</p>
            <h5>{item.location}</h5>
            <h3>{item.title}</h3>
            <h4>{item.institution}</h4>
          </div>
        {/each}
        <div>
          <h2>Education</h2>
        </div>
        {#each education as item}
          <div class="experience-item">
            <p>{item.date}</p>
            <h5>{item.location}</h5>
            <h3>{item.title}</h3>
            <h4>{item.institution}</h4>
          </div>
        {/each}
      </div>
    </div>
    <SectionJump href="#skills" />
  </section>
</main>

<style>
  section {
    margin-bottom: 7000px;
    padding: 20px;
    grid-column: 1 / 13;
    justify-content: center;
    align-items: center;
  }
  .experience-item {
    background-color: var(--main-color);
    border-radius: 20px;
    padding: 20px;
    margin: 30px;
    width: 100%;
  }

  @keyframes fadeIn {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }

  @media (prefers-reduced-motion: no-preference) {
    @supports (animation-timeline: scroll()) {
      .experience-item {
        animation: fadeIn 0.5s ease;
        animation-timeline: view();
      }
    }
  }

  .journey-container {
    padding-top: 50px;
    padding-bottom: 50px;
    width: 100%;
  }
  .col {
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 20px;
    align-items: center;
  }
  h3 {
    font-weight: bold;
    text-align: start;
    color: white;
    margin-bottom: 5px;
  }
  h2 {
    font-size: 2em;
    font-weight: bold;
    text-align: center;
    color: white;
    margin-bottom: 5px;
    width: 100%;
    font-family: "Courier New", Courier, monospace;
    font-weight: bold;
    text-align: center;
  }
</style>
