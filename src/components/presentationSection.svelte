<script lang="ts">
  import Img from "../assets/img.jpg";

  function scrollToSection() {
    // TODO: implement smoother scroll
    const section = document.getElementById("what-i-do");
    if (section) {
      section.scrollIntoView();
    }
  }
</script>

<main>
  <section id="presentation">
    <div class="row">
      <div class="col">
        <h1>Hi my name is Alejandro Lopez</h1>
        <h2>I'm a software engineer with a passion for system design</h2>
        <div class="button-container">
          <button on:click={scrollToSection}>Start</button>
        </div>
      </div>
      <div class="pic-container">
        <img class="pic" src={Img} alt="Alejandro Lopez" />
      </div>
    </div>
  </section>
</main>

<style>
  section {
    margin-bottom: 700px;
    padding: 20px;
    grid-column: 1 / 13;
    justify-content: end;
    align-items: center;    
  }

  .pic {
    width: 80%;
    height: auto;
  }

  .pic-container {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
  }

  button {
    width: 100%;
    background-color: var(--accent-color);
    color: white;
    padding: 10px 20px;
    margin-bottom: 50px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  @media only screen and (min-width: 768px) {
    /* For desktop: */
    section {
      grid-column: 1 / 13;
      margin-bottom: 700px;
      padding: 40px;
      background-color: var(--secondary-color);
    }
    .pic {
      width: 50%;
      height: auto;
      padding: 20px;
    }
    button:hover {
      background-color: var(--accent-color-dark);
    }

    .button-container {
      display: flex;
      padding-top: 20px;
      justify-content: start;
      align-items: center;
      width: 100%;
    }

    .col {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: start;
    }

    .row {
      display: flex;
      flex-direction: row;
      justify-content: space-around;
      align-items: center;
    }
  }
</style>
