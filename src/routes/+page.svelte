<script>
  import Landing from "$lib/Landing.svelte";
  import About from "$lib/About.svelte";
  import Projects from "$lib/Projects.svelte";
  import Contact from "$lib/Contact.svelte";
  import Skills from "$lib/Skills.svelte";
</script>

<Skills />
<Landing />
<div class="container">
  <About />
  <Projects />
  <Contact />
</div>

<style>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 80%;
    margin: 0 auto;
    padding: 20px;
    box-sizing: border-box;
  }
</style>
