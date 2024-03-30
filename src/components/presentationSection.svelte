<script lang="ts">
  import Img from "../assets/img.jpg";
</script>

<main>
  <div class="row">
    <div class="col">
      <h1>Hi my name is Alejandro Lopez</h1>
      <h2>
        I'm a software engineer with a passion for system design from Venezuela
      </h2>
      <div class="button-container">
        <button>Start</button>
      </div>
    </div>
    <img src={Img} alt="Alejandro Lopez" />
  </div>
</main>

<style>
  img {
    width: 20%;
    height: auto;
    padding: 20px;
  }

  button {
    width: 250px;
    background-color: var(--accent-color);
    color: white;
    padding: 10px 20px;
    margin-bottom: 50px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
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
    background-color: var(--secondary-color);
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
  }
</style>
