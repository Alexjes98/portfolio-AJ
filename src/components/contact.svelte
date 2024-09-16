<script>
  // @ts-nocheck
  import FaTelegramPlane from "svelte-icons/fa/FaTelegramPlane.svelte";
  import FaEnvelope from "svelte-icons/fa/FaEnvelope.svelte";
  import FaCommentAlt from "svelte-icons/fa/FaCommentAlt.svelte";
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
        <div class="row">
          <form
            action="mailto:{import.meta.env.VITE_EMAIL}"
            method="get"
            enctype="text/plain"
          >
            <button type="submit">
              <div class="ico">
                <FaEnvelope />
              </div>
            </button>
          </form>
          <button>
            <div class="ico">
              <a href="https://t.me/{import.meta.env.VITE_TELEGRAM}" target="_blank">
                <FaTelegramPlane />
              </a>
            </div>
          </button>
          <button>
            <div class="ico">
              <a href="https://wa.me/{import.meta.env.VITE_PHONE}" target="_blank">
                <FaCommentAlt />
              </a>
            </div>
          </button>
        </div>
      </div>
    </div>
  </section>
</main>

<style>
  .row{
    width: 100%;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
  }
  .ico {
    height: 25px;
  }
  section {    
    margin-bottom: 50px;
    padding: 20px;
    grid-column: 1 / 13;
  }
  .contact-form {
    display: flex;
    font-size: 1em;
    width: 100%;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    background-color: var(--main-color);
    border-radius: 10px;
    padding: 20px;
    margin-top: 20px;
  }
  .title {
    font-size: 2em;
    font-weight: bold;
    color: white;
    text-align: center;
  }
  button {
    width: 100px;
    padding: 10px;    
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  button:hover {
    background-color: var(--accent-color-dark);
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
