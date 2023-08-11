<script>
  import { onMount } from "svelte";
  import { fade } from "svelte/transition";

  let visible = false;

  onMount(() => {
    const aboutSection = document.getElementById("about");
    const observer = new IntersectionObserver(([entry]) => {
      visible = entry.isIntersecting;
    });

    observer.observe(aboutSection);

    return () => observer.disconnect(); // Cleanup
  });
</script>

{#if visible}
<div class="skills">
    <h2 transition:fade={{ delay: 100 }}>Skills</h2>
        <div class="skill" transition:fade={{ delay: 500 }}>
          <img src="/python.png" alt="Python" />
          <span>Python</span>
        <!-- Other skills with increasing delay -->
      </div>
    <div class="skill" transition:fade={{ delay: 750 }}>
      <img src="/js.png" alt="JavaScript" />
      <span>JavaScript</span>
    </div>
    <div class="skill" transition:fade={{ delay: 950 }}>
      <img src="/svelte.png" alt="Svelte" />
      <span>Svelte</span>
    </div>
    <!-- Add more skills as needed -->
  </div>
{/if}

<style>
  .skills {
    position: fixed; /* Fixed position */
    left: 0; /* Far left of the page */
    top: 20%; /* Adjust vertical position as needed */
    border-top: 2px solid blue;
    border-right: 2px solid blue;
    padding: 10px;
  }

  .skill {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 10px;
  }

  .skill img {
    width: 50px;
    height: 50px;
  }

  .skill span {
    font-size: 1rem;
    text-align: center;
  }
</style>
