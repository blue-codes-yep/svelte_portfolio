<script>
  import Landing from "$lib/Landing.svelte";
  import About from "$lib/About.svelte";
  import Projects from "$lib/Projects.svelte";
  import Contact from "$lib/Contact.svelte";
  import Skills from "$lib/Skills.svelte";
  import { theme } from '$lib/store';

  /**
     * @type {HTMLDivElement}
     */
  let containerElement;
  $: if (containerElement) {
    containerElement.dataset.theme = $theme;
  }
</script>

<Skills />
<div bind:this={containerElement} class="container">
  <Landing />
  <div class="background-text">
    <h1 class="title">Blue Codes</h1>
    <h2 class="subtitle">Software Engineer</h2>
  </div>
  <section id="about-me" class="main-section">
    <About />
  </section>
  <section id="projects" class="main-section">
    <Projects />
  </section>

  <section id="contact" class="main-section">
    <Contact />
  </section>
</div>

<style>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    margin: 0 auto;
    padding: 20px;
    box-sizing: border-box;
  }

  .main-section {
    margin-bottom: 40px;
    box-sizing: border-box;
  }

  #about-me {
    padding: 80px;
    margin-bottom: 350px;
    border: 2px solid var(--border-color);
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
    opacity: 0.95;
  }

  #about-me:hover {
    transform: scale(1.02);
    box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
  }

  .background-text {
    transition: color 0.5s, opacity 0.5s;
    position: absolute;
    top: 0;
    left: 0;
    opacity: 0.3;
    color: var(--background-text-color);
    cursor: default;
    z-index: 0;
    margin-top: 75px;
  }

  .background-text:hover {
    color: rgb(66, 66, 248);
    opacity: 0.5; /* You can adjust the opacity on hover if desired */
  }
  .title {
    font-size: 10rem;
    font-weight: bold;
    line-height: 1;
    margin: 0;
    animation: neonEffect 1s ease-in-out infinite alternate;
  }

  .subtitle {
    font-size: 2.1rem;
    font-weight: bold;
    line-height: 1;
    margin-left: 150px;
  }

  @keyframes neonEffect {
    from {
      text-shadow: 0 0 10px #0095ff, 0 0 20px #0095ff, 0 0 30px #0095ff;
    }
    to {
      text-shadow: 0 0 20px #0095ff, 0 0 30px #0095ff, 0 0 40px #0095ff;
    }
  }


  /* Responsive Styles */
  @media (max-width: 768px) {
    .container {
      margin-left: 50px;
    }

    #about-me {
      padding: 40px; /* Reduced padding */
      margin-top: 250px;
      margin-bottom: 200px; /* Reduced margin */
      /* Adjust other styles as needed */
    }
  }


</style>
