<script>
</script>

<main>
  <section id="contact">
    <div>
      <div class="title">
        <h2>Let's talk</h2>
        <p>
          Feel free to contact me if you have any questions or if you want to
          work with me
        </p>
      </div>
      <div class="contact-form">
        <div class="contact-content">
          <h4>Your Name:</h4>
          <input type="text" />        
          <h4>Your Email:</h4>
          <input type="text" />
          <h4>Your Message:</h4>
          <textarea></textarea>
        </div>
        <button>Send</button>
      </div>
    </div>
  </section>
</main>

<style>
  section {    
    margin-bottom: 50px;
    padding: 20px;
    grid-column: 1 / 13;
  }
  .contact-content {
    display: flex;
    flex-direction: column;
    align-items: start;
    justify-content: center;
    width: 100%;
  }
  
  .contact-form {
    display: flex;
    font-size: 1em;
    width: 50%;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color: var(--main-color);
    border-radius: 10px;
    padding: 20px;
  }
  .title {
    font-size: 2em;
    font-weight: bold;
    color: white;
    text-align: center;
  }
  h4 {
    font-weight: bold;
    color: white;
    font-family: "Courier New", Courier, monospace;
    margin-bottom: 5px;
  }
  button {
    width: 100px;
    padding: 10px;
    background-color: var(--accent-color);
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  input {
    width: 95%;
    padding: 10px;
    margin-bottom: 10px;
  }
  textarea {
    width: 95%;
    padding: 10px;
    margin-bottom: 10px;
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
