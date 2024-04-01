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
  <div class="journey-container">
    <div class="row">
      <div class="col">
        <h3>Education</h3>
        <div class="line-left" />
        <div class="circle-left" />
        <div class="circle-down-left" />
        {#each education as item}
          <div class="experience-item">
            <p>{item.date}</p>
            <h5>{item.location}</h5>
            <h3>{item.title}</h3>
            <h4>{item.institution}</h4>
          </div>
        {/each}
      </div>
      <div class="col">
        <h3>Experience</h3>
        <div class="line-right" />
        <div class="circle-right" />
        <div class="circle-down-right" />
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
  </div>
</main>

<style>
  .line-right {
    position: absolute;
    width: 5px;
    height: 550px;
    left: 0%;
    top: 15%;
    background-color: var(--main-color);
  }
  .line-left {
    position: absolute;
    width: 5px;
    height: 550px;
    left: 0%;
    top: 15%;
    background-color: var(--main-color);
  }
  .circle-right {
    position: absolute;
    width: 30px;
    height: 30px;
    left: -1.3%;
    top: 13%;
    border-radius: 50%;
    background-color: var(--main-color);
  }
  .circle-down-right {
    position: absolute;
    width: 30px;
    height: 30px;
    left: -1.3%;
    top: 53%;
    border-radius: 50%;
    background-color: var(--main-color);
  }
  .circle-left {
    position: absolute;
    width: 30px;
    height: 30px;
    left: -1.3%;
    top: 13%;
    border-radius: 50%;
    background-color: var(--main-color);
  }
  .circle-down-left {
    position: absolute;
    width: 30px;
    height: 30px;
    left: -1.3%;
    top: 53%;
    border-radius: 50%;
    background-color: var(--main-color);
  }
  .experience-item {
    border-radius: 25px;
    background-color: var(--accent-color-light);
    padding: 20px;
    width: 100%;
    margin-bottom: 20px;
  }
  .journey-container {
    position: relative;
    padding-inline: 20px;
    width: 100%;
    background-color: var(--background-color);
  }
  .row {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    flex: 2;
  }
  .col {
    display: flex;
    flex-direction: column;
    justify-content: start;
    align-items: start;
    flex: 2;
    margin-inline: 20px;
    padding: 20px;
    position: relative;
  }

  h3 {
    font-weight: bold;
    text-align: start;
    color: var(--main-color);
    margin-bottom: 30px;
  }
</style>
