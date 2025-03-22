<script lang="ts">
  import Img from "../assets/img.jpg";

  function scrollToSection() {
    // TODO: implement smoother scroll
    const section = document.getElementById("what-i-do");
    if (section) {
      section.scrollIntoView();
    }
  }
  let presentation = ">Hi, my name is ";
  let presentationRef = "";
  let name = "Alejandro Lopez";
  let nameRef = "";
  let presentationDelayed = ">I'm a software engineer with a passion for system design";
  let presentationDelayedRef = "";

  function typePresentation() {
    for (let i = 0; i <= presentation.length; i++) {
      setTimeout(() => {
        presentationRef = presentation.slice(0, i);
      }, 100 * i);
    }
    setTimeout(() => {
      for (let i = 0; i <= name.length; i++) {
        setTimeout(() => {
          nameRef = name.slice(0, i);
        }, 100 * i);
      }
    }, 100 * presentation.length);
    setTimeout(() => {
    for (let i = 0; i <= presentationDelayed.length; i++) {
      setTimeout(() => {
        presentationDelayedRef = presentationDelayed.slice(0, i);
        }, 100 * i);
      }
    }, 100 * presentation.length + 100 * name.length);
  }
  typePresentation();
</script>

<main>
  <section id="presentation">
    
      <div class="col">
        <div class="presentation-container">
          <h1>{presentationRef}<span class="name">{nameRef}</span></h1>
          <h2>{presentationDelayedRef}</h2>
        </div>        
      </div>
      <div class="row">
        <div class="pic-container">
          <img class="pic" src={Img} alt="Alejandro Lopez" loading="lazy"  />
        </div>
      </div>      
  </section>
</main>

<style>
  .name {
    color: #ff7b00;    
    font-weight: bold;
    text-shadow: 0 0 5px rgba(255, 81, 0, 0.952);
  }
  .presentation-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-color: #1e1e1e;
    margin-top: 50px;
    padding: 2rem;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
    border: 1px solid #333;
    width: 100%;    
  }

  .presentation-container h1, .presentation-container h2 {
    font-family: 'Courier New', monospace;
    color: #00b7ff;
    margin: 0.5rem 0;
    text-shadow: 0 0 5px rgb(0, 255, 255);
  }
  .presentation-container h2 {
    color: #00ccff;
  }

  .presentation-container h2::before {
    color: #00ccff;
  }

  section {
    margin-top: 70px;
    margin-bottom: 700px;
    padding: 20px;
    grid-column: 1 / 13;
    justify-content: end;
    align-items: center;    
  }
  .pic-container {
    display: flex;
    justify-content: center;
    align-items: center;
    animation: fadeIn 8s ease-in-out;
  }

  .pic {
    margin-top: 100px;
    width: 50%;
    height: 50%;
    object-fit: cover;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
    border: 1px solid #333;
  }

  @keyframes fadeIn {
    from {
      opacity: 0;      
    }
    to {
      opacity: 0.5;      
    }
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
      margin-bottom: 7000px;
      padding: 40px;
      background-color: var(--secondary-color);
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
      justify-content: space-between;
      align-items: center;
    }
  }
</style>
