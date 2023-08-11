<script>
    import { onMount } from "svelte";
  
    let words = ["Welcome", "Scroll down", "to check me out"];
    let currentWord = 0;
    let visible = false;
  
    onMount(() => {
      const interval = setInterval(() => {
        visible = !visible; // Toggle visibility
        if (visible) {
          currentWord = (currentWord + 1) % words.length; // Change word when becoming visible
        }
      }, 1000); // Toggle visibility every second
  
      return () => clearInterval(interval); // Cleanup
    });
  </script>
  
  <div class="landing">
    <h1 class={visible ? 'visible' : ''}>{words[currentWord]}</h1>
    <p>Explore my portfolio and learn more about me.</p>
  </div>
  
  <style>
    .landing {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      background-color: var(--background-color);
      text-align: center;
    }
  
    .landing h1 {
      font-size: 2.5rem;
      transition: opacity 0.5s;
      opacity: 0;
    }
  
    .landing h1.visible {
      opacity: 1;
    }
  
    .landing p {
      font-size: 1.2rem;
    }
  </style>