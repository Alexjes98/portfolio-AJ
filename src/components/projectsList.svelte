<script>
  // @ts-nocheck

  import FaInfo from "svelte-icons/fa/FaInfo.svelte";
  import ProjectItem from "./projectItem.svelte";
  let show = false;
</script>

<main>
  <section id="projects-list">
    <div class="title">
      <h2>Some of my latest projects</h2>
      <a href="#freddaid">Start</a>
    </div>
    <div class="project-list">
      <div
      style="height: 11100px; width: 50px; background-color: red;"
      >MARGIN</div>
      <ProjectItem
        id="freddaid"
        imgSrc="clew.png"
        nextId="#sales-factory"
        title="Sales Factory - FreddAid"
        description="I worked for Sales Factory developing a chatbot that uses RAG (Retrieval Augmented Generation) to answer questions about different Sales Factory Clients data and services.
        The chatbot is deployed in Azure and uses Azure functions to run a Langchain agent in python that uses OpenAI to generate answers.
        The chatbot also uses Azure Cognitive Search to index the data and generate the embeddings, and an Azure retrieval function to get the data from the index.
        The web app is developed in React and uses Microsoft B2C for authentication and CosmosDB as the database."
        technologies={[
          "React",
          "Azure",
          "Python",
          "Azure functions",
          "Cognitive Search",
          "OpenAI",
          "Langchain",
          "CosmosDB",
          "Microsoft B2C",
        ]}
      />
      <ProjectItem
        id="sales-factory"
        imgSrc="skynet.png"
        prevId="#freddaid"
        nextId="#stipe"
        title="Sales Factory"
        description="I worked for Sales Factory developing an administrative web app in React, 
        the App is used to administrate budgets and allocations for marketing campaigns.
        Is deployed with AWS Amplify and uses Cognito for authentication, S3 for file storage,
        and Express.js for the backend server with Postgres as the database.
        The app also uses Cypress and Jest for testing following TDD practices."
        technologies={[
          "React",
          "Amplify",
          "Cypress",
          "Express.js",
          "Jest",
          "Node.js",
          "Postgres",
          "Cognito",
          "S3",
        ]}
      />

      <ProjectItem
        id="stipe"
        imgSrc="stipe.png"
        prevId="#sales-factory"
        nextId="#little-bellies"
        title="Stipe"
        description="Stipe is a project that I developed for a little company in Guatemala,
        It was my first project working for a company not as a freelancer. The full project consists of a Flutter mobile app,
        a postgres database, a node.js backend server, and a web app in React"
        technologies={[
          "Flutter",
          "Node.js",
          "Postgres",
          "React",
          "EC2",
          "Amplify",
        ]}
      />
      <ProjectItem
        id="little-bellies"
        imgSrc="littlebellies.png"
        prevId="#stipe"
        nextId="#progressive-label"
        title="Little Bellies"
        description="Little Bellies is a project in wich I worked developing Cypress tests for the web app,
        the project consists of a web app in React, a node.js backend server, and a DynamoDB database"
        technologies={["Cypress", "Node.js", "DynamoDB", "Postgres", "React"]}
      />
      <ProjectItem
        id="progressive-label"
        imgSrc="progressive.png"
        prevId="#little-bellies"
        title="Progressive Label"
        description="I worked for Progressive Label developing Cypress tests for the Frontend and Jest test for the backend server.
        The web app consists of a service to generate labels for products and manage the creation process for those labels.
        The app is developed in Remix and uses Postgres as the database, the backend server is developed in Node.js and Express.js.
        "
        technologies={[
          "Cypress",
          "Jest",
          "Node.js",
          "Express.js",
          "Remix",
          "Postgres",
          "Cognito",
          "S3",
        ]}
      />
    </div>
  </section>
</main>

<style>
  .title {
    font-size: 2em;
    font-weight: bold;
    color: white;
    text-align: center;
    margin-bottom: 5000px;
  }
  .project-list {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    flex-direction: column;
    padding: 10px;
  }
  section {
    padding: 20px;
    grid-column: 1 / 13;
    justify-content: end;
    align-items: center;
  }
  h2 {
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
