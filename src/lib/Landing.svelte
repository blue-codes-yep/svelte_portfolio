<script>
  import { onMount } from "svelte";
  import * as animateScroll from "svelte-scrollto";

  let words = ["Welcome", "Check out my projects!"];
  let currentWord = 0;
  let visible = false;
  let showText = false;

  onMount(() => {
    setTimeout(() => {
      showText = true;
    }, 1000); // 1 second delay

    setTimeout(() => {
      animateScroll.scrollTo({ element: "#projects", duration: 2000 });
    }, 2500); // 2 seconds delay
  });
</script>

<div class="landing">
  <div class="TextContainer">
    <a href="#projects" class="continue-link" >
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
    {#if showText}
      <div class="animated-text"><h2>Check out my projects</h2></div>
    {/if}
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


  .animated-text {
  position: relative;
  left: -80%;
  transform: translateY(-50%);
  font-size: 1.5rem;
  text-align: center;
  opacity: 0;
  color: #000;
  text-shadow: none;
  animation: 
    slideIn 2s forwards, 
    fadeIn 2s forwards, 
    bounce 2s 1.5s ease-in-out infinite, 
    colorChange 4s infinite, 
    textShadow 4s infinite;
}
@keyframes slideIn {
  100% {
    left: 50%;
    transform: translate(-50%, -50%);
  }
}

@keyframes fadeIn {
  100% {
    opacity: 1;
  }
}


@keyframes colorChange {
  0%, 100% {
    color: #000;
  }
  50% {
    color: #f00;
  }
}

@keyframes textShadow {
  0%, 100% {
    text-shadow: none;
  }
  50% {
    text-shadow: 2px 2px 4px #000;
  }
}
</style>
