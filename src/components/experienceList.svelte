<script lang="ts">
  // @ts-nocheck
  import FaDatabase from "svelte-icons/fa/FaDatabase.svelte";
  import FaMobileAlt from "svelte-icons/fa/FaMobileAlt.svelte";
  import FaCloud from "svelte-icons/fa/FaCloud.svelte";
  import FaCode from "svelte-icons/fa/FaCode.svelte";
</script>

<main>
  <section id="what-i-do">
    <div class="experience-container">
      <div
      class="title"
      >
        <h2>What I Do</h2>
      </div>
      <div class="experience-list">
        <div class="experience-item">
          <div class="icon">
            <FaCode />
          </div>
          <h3>Front-End Development</h3>
          <p>
            I have experience with HTML, CSS, and JavaScript, and I have worked
            with React, Material UI, Remix, Svelte, and Testing Libraries like
            Jest and Cypress to create responsive and interactive user
            interfaces
          </p>
        </div>
        <div class="experience-item">
          <div class="icon">
            <FaDatabase />
          </div>
          <h3>Back-End Development</h3>
          <p>
            I have experience with Node.js, Express.js, JWT, ORMs like Sequelize
            and using dependency injection, and design patterns to create secure
            APIs for robust web applications with database services like
            MongoDB, MySQL, and Postgres
          </p>
        </div>
        <div class="experience-item">
          <div class="icon">
            <FaCloud />
          </div>
          <h3>Cloud Development</h3>
          <p>
            I have experience with AWS services like EC2, S3, RDS, Lambda,
            ElasticBeanstalk, Amplify, Cognito and Azure services like Blob
            Storage, Cosmos DB, Functions, and I have used them to deploy and
            scale web applications
          </p>
        </div>
        <div class="experience-item">
          <div class="icon">
            <FaMobileAlt />
          </div>
          <h3>Android iOS Development</h3>
          <p>
            I have experience with Flutter and BaaS platforms like Firebase
            configuring services like Firestore, Authentication, Notifications,
            and Cloud Storage to create mobile applications for Android and iOS
            devices
          </p>
        </div>
      </div>
    </div>
  </section>
</main>

<style>
  .title {
    font-size: 2em;
    font-weight: bold;
    color: white;
    text-align: center;
    margin-bottom: 100px;    
  }
  section {
    margin-bottom: 1000px;
    padding: 20px;
    grid-column: 1 / 13;
  }
  p {
    font-family: "Courier New", Courier, monospace;
    font-weight: bold;
    text-align: justify;
  }
  h3 {
    font-weight: bold;
    text-align: center;
  }
  h2 {
    width: 100%;
    font-family: "Courier New", Courier, monospace;
    font-weight: bold;
    text-align: center;
  }
  .icon {
    width: 100%;
    height: 54px;
    color: white;
    margin-bottom: 10px;
  }
  .experience-container {    
    width: 100%;
  }

  .experience-list {
    width: 100%;
    justify-content: center;
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
  }

  .experience-item {
    background-color: var(--main-color);
    padding: 20px;
    border: 5px solid #ccc;
    border-radius: 15px;
    width: 350px;
  }
</style>
