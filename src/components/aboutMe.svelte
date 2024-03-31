<script>
  // @ts-nocheck

  import AboutImg from "../assets/about_img.png";

  import DiGithubBadge from "svelte-icons/di/DiGithubBadge.svelte";
  import FaLinkedin from "svelte-icons/fa/FaLinkedin.svelte";
  import FaInstagram from "svelte-icons/fa/FaInstagram.svelte";

  import FaStar from "svelte-icons/fa/FaStar.svelte";
</script>

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
          <img src={AboutImg} alt="profile" aria-label="profile" />
        </div>
        <div class="col">
          <h1>Code Architect, Problem Solver</h1>
          <h4>
            I am a software engineer graduated from the National Experimental
            University of Táchira. (UNET) I have worked in the development of
            web applications, mobile applications, and cloud services since my
            lasts years in college.
          </h4>
          <div class="icons-row">
            <div class="icon">
              <a href="https://github.com/Alexjes98">
                <DiGithubBadge />
              </a>
            </div>
            <div class="icon">
              <a href="https://www.linkedin.com/in/alejandro-lopez-9b3462179/">
                <FaLinkedin />
              </a>
            </div>
            <div class="icon">
              <a href="https://www.instagram.com/alexandre_dupre98/">
                <FaInstagram />
              </a>
            </div>
            <div class="download-container">
              <button> Download CV </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</main>

<style>
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
    width: 110%;
    bottom: 0;
    left: -10px;
    height: 33px;
    background-color: var(--main-color);
  }
  .icons-row {
    display: flex;
    justify-content: space-around;
    align-items: center;
    width: 100%;
  }
  button {
    background-color: var(--accent-color);
    color: var(--secondary-color);
    border: none;
    width: 100%;
    padding: 10px 20px;
    border-radius: 5px;
    cursor: pointer;
  }
  button:hover {
    background-color: var(--accent-color-dark);
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
  .download-container {
    align-self: flex-end;
    width: 100%;
    height: 54px;
    margin-bottom: 70px;
    margin-right: 20px;
  }

  .avatar {
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: var(--background-color);
    width: 500px;
    height: 500px;
    border-radius: 500px;
    overflow: hidden;
  }
  img {
    width: 100%;
    height: auto;
    padding: 20px;
  }
  h2 {
    font-family: "Courier New", Courier, monospace;
    font-weight: bold;
    text-align: center;
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
    justify-content: center;
    align-items: start;
    flex: 2;
    margin-inline: 20px;
  }
  .about-container {
    position: relative;
    padding-inline: 20px;
    margin-top: 80px;
    width: 100%;
    background-color: var(--secondary-color);
  }
  h2,
  h4,
  h1 {
    color: var(--background-color);
  }
</style>
