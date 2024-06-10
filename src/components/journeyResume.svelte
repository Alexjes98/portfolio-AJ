<script>
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
  <section>
    <div class="journey-container">
        <div class="col">
          <div>
            <h2>Education</h2>
          </div>
          <div />
          <div />
          <div />
          {#each education as item}
            <div class="experience-item">
              <p>{item.date}</p>
              <h5>{item.location}</h5>
              <h3>{item.title}</h3>
              <h4>{item.institution}</h4>
            </div>
          {/each}
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
        </div>
      </div>
  </section>
</main>

<style>
  .experience-item {
    background-color: var(--main-color);
    padding: 20px;
    width: 100%;
    margin-bottom: 50px;
  }
  
  .journey-container {
    position: relative;    
    padding-top: 50px;
    padding-bottom: 50px;
    margin-top: 80px;
    width: 100%;
  }
  .col {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: start;    
  }
  section {
    margin-bottom: 500px;
  }

  h3 {
    font-weight: bold;
    text-align: start;
    color: white;
    margin-bottom: 5px;
  }
  h2{
    font-weight: bold;
    text-align: center;
    color: var(--main-color);
    margin-bottom: 5px;
  }
</style>
