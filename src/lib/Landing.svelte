<script>
  import { onMount } from "svelte";
  // @ts-ignore
  import * as animateScroll from "svelte-scrollto";



  onMount(() => {
    setTimeout(() => {
      animateScroll.scrollTo({ element: "#projects", duration: 2000 });
    }, 2500); 
  });
</script>

<div class="landing">
  <div class="TextContainer">

  </div>

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

  .landing .TextContainer {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 40vh;

    text-align: center;
  }

</style>
