<script>
  // @ts-nocheck
  import FaAngleDown from "svelte-icons/fa/FaAngleDown.svelte";

  export var href = "";
</script>

<main>
  <div class="jump-row">
    <div class="jump-icon">
      <a {href}>
        <FaAngleDown />
      </a>
    </div>
  </div>
</main>

<style>
  .jump-row {
    display: flex;
    justify-content: center;
    align-items: end;
    flex-direction: column;
    width: 100%;
  }

  @media (prefers-reduced-motion: no-preference) {
    .jump-icon {
      animation: bounce 1s ease infinite;
    }
  }

  .jump-icon {
    color: var(--background-color);
    width: 50px;
    height: 50px;
  }

  @keyframes bounce {
    70% {
      transform: translateY(0%);
    }
    80% {
      transform: translateY(-15%);
    }
    90% {
      transform: translateY(0%);
    }
    95% {
      transform: translateY(-7%);
    }
    97% {
      transform: translateY(0%);
    }
    99% {
      transform: translateY(-3%);
    }
    100% {
      transform: translateY(0);
    }
  }

  .jump-icon:hover {
    color: var(--accent-color);
  }
</style>
