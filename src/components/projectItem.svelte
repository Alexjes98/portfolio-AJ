<script>
  // @ts-nocheck
  import FaInfo from "svelte-icons/fa/FaInfo.svelte";
  let show = true;
  export let title;
  export let imgSrc;
  export let description;
  export let technologies;
  export let id;
  export let nextId;
  export let prevId;
</script>

<div {id} class={`project-element ${show ? "" : "invisible-container"}`}>
  <div class="project-element-header">
    <h2>
      {title}
    </h2>
    <button class="btn" on:click={() => (show = !show)}>
      <div class="ico">
        <FaInfo />
      </div>
    </button>
  </div>
  <div>
    {#if show}
      <div class="row">
        <div class="col">
          <h4>Tecnologies</h4>
          <b>
            {#each technologies as technologie}
              <b>{technologie}, </b>
            {/each}
          </b>
          <p>
            {description}
          </p>
          <div class="row">
            {#if prevId}
              <a href={prevId}>Back</a>
            {/if}
            {#if nextId}
              <a href={nextId}>Next</a>
            {/if}
          </div>
        </div>
        <img src={imgSrc} alt={title} />
      </div>
    {/if}
  </div>
</div>

<style>
  .col {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    padding: 5px;
  }
  .row {
    display: flex;
    flex-direction: row;
    justify-content: space-between;    
  }
  img {
    width: 70%;
    height: 100%;
    object-fit: cover;
  }
  .invisible-container {
    margin-bottom: 1000px;
  }
  .ico {
    height: 25px;
  }
  .btn {
    background-color: transparent;
    border: none;
    color: white;
    cursor: pointer;
  }
  .btn:hover {
    color: var(--accent-color);
  }
  .btn:active,
  .btn:focus {
    outline: none;
    background: none;
    color: inherit;
  }
  .project-element {    
    text-align: justify;
    padding: 20px;
    background-color: var(--main-color);
    border-radius: 5px;
  }
  @media only screen and (min-width: 768px) {
    /* For desktop: */
    .project-element {
      text-align: left;
      background-color: var(--main-color);
      border-radius: 5px;
      margin-bottom: 3600px;
    }
    .project-element-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      background-color: var(--main-color);
      color: white;
      border-radius: 5px;
      padding: 10px;
    }
  }
</style>
