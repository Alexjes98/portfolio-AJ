<script>
  // @ts-nocheck
  import AboutImg from "../assets/about_img.png";
  import AIPractitoner from "../assets/aws-certified-ai-practitioner.webp";
  import CloudPractitoner from "../assets/aws-certified-cloud-practitioner.webp";
  import CloudDeveloper from "../assets/aws-certified-developer-associate.webp";

  import DiGithubBadge from "svelte-icons/di/DiGithubBadge.svelte";
  import FaLinkedin from "svelte-icons/fa/FaLinkedin.svelte";
  import FaInstagram from "svelte-icons/fa/FaInstagram.svelte";
  import FaStar from "svelte-icons/fa/FaStar.svelte";
  
  import SectionJump from "./common/sectionJump.svelte";

  let scrollY = 0;
  let isStarted = false;
  
  const title = "Code Architect, Problem Solver";
  let titleRef = "";
  const description = "I am a software engineer graduated from the National Experimental University of Táchira. (UNET) I have worked in the development of web applications, mobile applications, and cloud services since my lasts years in college.";
  let descriptionRef = "";  

  function typePresentation() {
    for (let i = 0; i <= title.length; i++) {
      setTimeout(() => {
        titleRef = title.slice(0, i);
      }, 50 * i);
    }
    setTimeout(() => {
      for (let i = 0; i <= description.length; i++) {
        setTimeout(() => {
          descriptionRef = description.slice(0, i);
        }, 20 * i);
      }
    }, 100 * title.length);    
  }
  $: {    
    if (scrollY > 8000 && !isStarted) {
      isStarted = true;
      typePresentation();
    }
  }
</script>

<svelte:window bind:scrollY />

<main>
  <section id="about-me">
    <div class="about-container">
      <div class="decoration-div" />
      <div class="decoration-icon">
        <FaStar />
      </div>
      <h2>About Me</h2>
      <div class="row">
        <div class="avatar">
          <img src={AboutImg} alt="profile" aria-label="profile" loading="lazy" />
        </div>
        <div class="col">
          <div class="console-container">
            <h1>{titleRef}</h1>
            <p>{descriptionRef}</p>
          </div>          
          <div class="icons-row">
            <div class="icon">
              <a href="https://github.com/Alexjes98" target="_blank">
                <DiGithubBadge />
              </a>
            </div>
            <div class="icon">
              <a
                href="https://www.linkedin.com/in/alejandro-lopez-9b3462179/"
                target="_blank"
              >
                <FaLinkedin />
              </a>
            </div>
            <div class="icon">
              <a
                href="https://www.instagram.com/alexandre_dupre98/"
                target="_blank"
              >
                <FaInstagram />
              </a>
            </div>
            <div class="resume-button">
              <a
                href="/CV.pdf"
                target="_blank"
                download
                class="download-button"
              >
                Resume
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="certifications">
      <div class="certification">
        <img src={CloudPractitoner} alt="Cloud Practitoner" />
        <div>
          <h2>Issued by AWS on 2022</h2>
        </div>
      </div>
      <div class="certification">
        <img src={AIPractitoner} alt="AI Practitoner" />
        <h2>Issued by AWS on 2024</h2>
      </div>
      <div class="certification">
        <img src={CloudDeveloper} alt="Cloud Developer" />
        <h2>Issued by AWS on 2025</h2>
      </div>
    </div>
    <SectionJump href="#journey-resume" />
  </section>
</main>

<style>
  section {
    margin-bottom: 200px;
    padding-top: 100px;
    grid-column: 1 / 13;
  }
  @keyframes fancy-in {
    /* card entry */
    0% {
      transform: translateX(90%) scale(1);
      opacity: 0;
    }
    /* card on stage */
    20%,
    80% {
      opacity: 1;
      transform: none;
    }
    /* card exit */
    100% {
      transform: translateX(10);
    }
  }
  @media (prefers-reduced-motion: no-preference) {
    @supports (animation-timeline: scroll()) {
      .certification {
        /*animation: fancy-in 1s both;
        animation-timeline: view();
        animation-range: contain;*/
      }
    }
  }
  .download-button {
    background-color: var(--accent-color);
    color: var(--white);
    border: none;
    width: 100%;
    padding: 10px 20px;
    border-radius: 5px;
    cursor: pointer;
  }
  .resume-button {
    width: 100%;
    height: 54px;
    color: white;
    margin: 0;
  }
  .certifications {
    display: flex;
    justify-content: space-around;
    align-items: center;
    flex-direction: column;
    width: 100%;
    margin-top: 50px;
  }
  .certification {
    width: 350px;
    height: 250px;
    margin-top: 250px;
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  .console-container h1,
  .console-container p {
    font-family: "Courier New", monospace;
    color: #00b7ff;
    margin: 0.5rem 0;
    text-shadow: 0 0 5px rgb(0, 225, 255);
  }

  .console-container h1 {
    font-size: 2rem;
    font-weight: bold;
  }
  .decoration-icon {
    position: absolute;
    z-index: 0;
    bottom: 5%;
    left: 0%;
    width: 50px;
    height: 50px;
    color: var(--white);
    rotate: 90deg;
  }
  .decoration-div {
    position: absolute;
    z-index: 2;
    width: 10%;
    bottom: 0;
    height: 33px;
    background-color: var(--main-color);
  }
  .icons-row {
    display: flex;
    justify-content: space-around;
    align-items: center;
    width: 100%;
  } 
  a {
    text-decoration: none;
    color: white;
  }
  a:hover {
    color: var(--main-color);
  }
  .icon {
    width: 100%;
    height: 54px;
    color: white;
    margin-bottom: 70px;
    margin-right: 20px;
  }

  .row {
    align-items: center;
    display: flex;
    flex-direction: column;
    text-align: center;
  }

  .avatar {
    display: flex;
    justify-content: center;    
    align-items: center;
    background-color: var(--main-color);
    width: 250px;
    height: 250px;
    border-radius: 50px;
    overflow: hidden;
  }
  img {
    width: 100%;
    height: auto;
  }
  h2 {
    font-size: 2em;
    font-family: "Courier New", Courier, monospace;
    font-weight: bold;
    text-align: center;
  }

  .col {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: start;
    flex: 2;
    margin-inline: 20px;
  }

  
  .about-container {
    position: relative;
    padding-top: 1px;
    padding-bottom: 5px;
    margin-top: 80px;
    width: 100%;
    background-color: var(--secondary-color);
  }
  h2,
  h1 {
    color: var(--background-color);
  }
  @media only screen and (min-width: 768px) {
    .avatar {
      width: 300px;
      height: 300px;
      border-radius: 300px;
    }

    .row {
      display: flex;
      flex-direction: row;
      justify-content: space-around;
      align-items: center;
      flex: 2;
    }
  }
</style>
