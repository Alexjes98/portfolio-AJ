<script>
  // @ts-nocheck
  import FaGithub from 'svelte-icons/fa/FaGithub.svelte'
  import awsDeveloper from '../../assets/aws-certified-developer-associate.webp'
  import awsPractitioner from '../../assets/aws-certified-cloud-practitioner.webp'
  import awsAI from '../../assets/aws-certified-ai-practitioner.webp'
  
  let show = false;
</script>

<main>
  <header>
    <nav class="border-gray-200">
      <div
        class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4"
      >
        <div class="flex items-center space-x-3 rtl:space-x-reverse">
          <a
            href="https://github.com/Alexjes98/"
            class="flex items-center"
          >
            <FaGithub />
          </a>
          <div class="flex items-center space-x-2">
            <img src={awsDeveloper} alt="AWS Certified Developer Associate" class="h-10 w-auto" />
            <img src={awsPractitioner} alt="AWS Certified Cloud Practitioner" class="h-10 w-auto" />
            <img src={awsAI} alt="AWS Certified AI Practitioner" class="h-10 w-auto" />
          </div>
        </div>
        <button
          on:click={() => (show = !show)}
          data-collapse-toggle="navbar-default"
          type="button"
          class="inline-flex items-center p-2 w-10 h-10 justify-center text-sm text-gray-500 rounded-lg md:hidden dark:focus:ring-gray-600"
          aria-controls="navbar-default"
          aria-expanded="false"
        >
          <span class="sr-only">Open main menu</span>
          <svg
            class="w-5 h-5"
            aria-hidden="true"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 17 14"
          >
            <path
              stroke="currentColor"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M1 1h15M1 7h15M1 13h15"
            />
          </svg>
        </button>
        <div
          class={` ${show ? "block" : "hidden"}
       w-full md:block md:w-auto`}
          id="navbar-default"
        >
          <ul
            class="font-medium flex flex-col p-4 md:p-0 mt-4 border border-gray-100 rounded-lg md:flex-row md:space-x-8 rtl:space-x-reverse md:mt-0 md:border-0 dark:border-gray-700"
          >
            <li>
              <a
                href="#presentation"
                class="block py-2 px-3 text-white bg-blue-700 rounded md:bg-transparent md:text-blue-700 md:p-0 dark:text-white md:dark:text-blue-500"
                aria-current="page">Home</a
              >
            </li>
            <li>
              <a
                href="#what-i-do"
                class="block py-2 px-3 text-gray-900 rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-blue-700 md:p-0 dark:text-white md:dark:hover:text-blue-500 dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent"
                >What I Do</a
              >
            </li>
            <li>
              <a
                href="#projects-list"
                class="block py-2 px-3 text-gray-900 rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-blue-700 md:p-0 dark:text-white md:dark:hover:text-blue-500 dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent"
                >Projects</a
              >
            </li>
            <li>
              <a
                href="#about-me"
                class="block py-2 px-3 text-gray-900 rounded md:border-0 md:hover:text-blue-700 md:p-0 dark:text-white md:dark:hover:text-blue-500 dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent"
                >About Me</a
              >
            </li>
            <li>
              <a
                href="#journey-resume"
                class="block py-2 px-3 text-gray-900 rounded md:border-0 md:hover:text-blue-700 md:p-0 dark:text-white md:dark:hover:text-blue-500 dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent"
                >My Journey</a
              >
            </li>
            <li>
              <a
                href="#skills"
                class="block py-2 px-3 text-gray-900 rounded md:border-0 md:hover:text-blue-700 md:p-0 dark:text-white dark:hover:text-white"
                >Skills</a
              >
            </li>
            <li>
              <a
                href="#contact"
                class="block py-2 px-3 text-gray-900 rounded md:border-0 md:hover:text-blue-700 md:p-0 dark:text-white md:dark:hover:text-blue-500 dark:hover:text-white"
                >Contact</a
              >
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>
</main>

<style>
  nav {
    background-color: var(--secondary-color);
    overflow: hidden;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 9;
  }

  nav a {
    color: #f2f2f2;    
    height: 2rem;
  }

  nav a:hover {
    background-color: #ddd;
    color: black;
  }
</style>
