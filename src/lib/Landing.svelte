<script>
  import { onMount } from "svelte";
  import * as animateScroll from 'svelte-scrollto';

  let words = ["Welcome", "Scroll down || Click", "to check me out"];
  let currentWord = 0;
  let visible = false;

  onMount(() => {
    const interval = setInterval(() => {
      visible = !visible; // Toggle visibility
      if (visible) {
        currentWord = (currentWord + 1) % words.length; // Change word when becoming visible
      }
    }, 1200); // Toggle visibility every second

    

    setTimeout(() => {
      animateScroll.scrollTo({ element: '#projects', duration: 2000 });
    }, 1250);  // 2000 milliseconds = 2 seconds
  });

  const scrollToProjects = () => {
  animateScroll.scrollTo({ element: '#projects', duration: 2000 });
};
</script>

<div class="landing">
  <div class="TextContainer">
    <a href="#projects" class="continue-link" on:click={scrollToProjects}>
      <h1 class={visible ? "visible" : ""}>{words[currentWord]}</h1>
      <svg
        class={visible ? "visible scroll-icon" : "scroll-icon"}
        width="200"
        height="200"
        viewBox="0 0 28.80 28.80"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
        ><g id="SVGRepo_bgCarrier" stroke-width="0" /><g
          id="SVGRepo_tracerCarrier"
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke="#aab6ee"
          stroke-width="0.048"
        /><g id="SVGRepo_iconCarrier">
          <path
            d="M12 6.5L12 17"
            stroke="#363853"
            stroke-width="1.5"
            stroke-linecap="round"
            stroke-linejoin="round"
          />
          <path
            d="M16 12.9117L12 17.5L8 12.9117"
            stroke="#0095FF"
            stroke-width="1.5"
            stroke-linecap="round"
            stroke-linejoin="round"
          />
        </g></svg
      >
    </a>
  </div>
  <p>Explore my portfolio and learn more about me.</p>
</div>

<style>
  .landing {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    text-align: center;
  }

  .landing h1 {

    font-size: 4.5rem;
    transition: opacity 0.5s;
    opacity: 0;
    filter: brightness(1.2);
    animation: neon-text 1s ease-in-out infinite alternate;
  }

  .landing h1.visible {
    opacity: 1;
  }

  @keyframes neon-text {
    from {
      filter: brightness(1.2) drop-shadow(0 0 5px var(--neon-color-text));
    }
    to {
      filter: brightness(1.3) drop-shadow(0 0 10px var(--neon-color-text));
    }
  }

  .landing p {
    font-size: 1.2rem;
  }

  .landing .TextContainer {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 40vh;

    text-align: center;
  }

  .continue-link {
    text-decoration: none;
    color: var(--text-color);
    font-size: 1.2rem;
    margin-top: 10px;
    cursor: pointer;
  }

  .scroll-icon {
    transition: opacity 1s;
    opacity: 0;
    filter: brightness(1.5);
    animation: neon 1s ease-in-out infinite alternate;
  }

  .scroll-icon.visible {
    opacity: 1;
  }

  @keyframes neon {
    from {
      filter: brightness(1.5) drop-shadow(0 0 10px var(--neon-color));
    }
    to {
      filter: brightness(2) drop-shadow(0 0 20px var(--neon-color));
    }
  }
</style>
