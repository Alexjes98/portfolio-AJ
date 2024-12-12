<script>
  // @ts-nocheck
  import FaInfo from "svelte-icons/fa/FaInfo.svelte";
  let show = true;
  export let title;
  export let images = [];
  export let description;
  export let technologies;
  export let id;
  export let nextId;
  export let prevId;

  import { onMount } from "svelte";

  export let height = "40rem"; // Default height, can be overridden

  let currentIndex = 0;

  function nextSlide() {
    currentIndex = (currentIndex + 1) % images.length;
  }

  function prevSlide() {
    currentIndex = (currentIndex - 1 + images.length) % images.length;
  }

  onMount(() => {
    const interval = setInterval(nextSlide, 5000); // Auto-advance every 5 seconds
    return () => clearInterval(interval);
  });
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
      <div class="column">
        <div style="margin-bottom: 15px;" class="col-span-4 row-span-1">
          <b>
            {#each technologies as technologie}
              <b>{technologie}, </b>
            {/each}
          </b>
        </div>
        <div class="row">
          <div
            class="relative w-full max-w-4x3 mx-auto overflow-hidden rounded-lg shadow-lg"
            style="height: {height};"
          >
            {#each images as image, index}
              <img
                src={"/" + image}
                alt={`Slide ${index + 1}`}
                class="absolute top-0 left-0 w-full h-full object-contain transition-opacity duration-500 ease-in-out"
                style="opacity: {index === currentIndex
                  ? 1
                  : 0}; pointer-events: {index === currentIndex
                  ? 'auto'
                  : 'none'};"
              />
            {/each}
            <button
              on:click={prevSlide}
              class="absolute left-2 top-1/2 transform -translate-y-1/2 bg-white bg-opacity-50 hover:bg-opacity-75 rounded-full p-2 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-primary z-10"
              aria-label="Previous slide"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-6 w-6"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M15 19l-7-7 7-7"
                />
              </svg>
            </button>

            <button
              on:click={nextSlide}
              class="absolute right-2 top-1/2 transform -translate-y-1/2 bg-white bg-opacity-50 hover:bg-opacity-75 rounded-full p-2 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-primary z-10"
              aria-label="Next slide"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-6 w-6"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 5l7 7-7 7"
                />
              </svg>
            </button>

            <div
              class="absolute bottom-4 left-0 right-0 flex justify-center space-x-2 z-10"
            >
              {#each images as _, index}
                <button
                  on:click={() => (currentIndex = index)}
                  class="w-3 h-3 rounded-full focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-primary"
                  class:bg-blue-700={index === currentIndex}
                  class:bg-gray-300={index !== currentIndex}
                  aria-label={`Go to slide ${index + 1}`}
                ></button>
              {/each}
            </div>
          </div>
        </div>
        <div class="column">
          <p class="text-start">
            {description}
          </p>
          <div class="links-row">
            {#if prevId}
              <a href={prevId}>Back</a>
            {/if}
            {#if !prevId || !nextId}
              <div></div>
            {/if}
            {#if nextId}
              <a href={nextId}>Next</a>
            {/if}
          </div>
        </div>
      </div>
    {/if}
  </div>
</div>

<style>
  .row{
    display: flex;
    justify-content: space-between;
    width: 100%;
  }
  .column{
    display: flex;
    flex-direction: column;
  }
  .links-row {
    display: flex;
    font-weight: bold;
    justify-content: space-between;
    margin-top: 10px;
  }
  a {
    color: white;
    text-decoration: none;
  }
  a:hover {
    color: var(--accent-color);
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
  .project-element-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      background-color: var(--main-color);
      color: white;
      border-radius: 5px;
      padding: 10px;
    }

    .project-element {
      text-align: left;
      background-color: var(--main-color);
      border-radius: 5px;
      margin-bottom: 4500px;
    }
  @media only screen and (min-width: 768px) {
    .project-element {
      margin-bottom: 3600px;
    }
    
  }
</style>
