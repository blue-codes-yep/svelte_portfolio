<script>
  import Nav from "$lib/Nav.svelte";
  import About from "$lib/About.svelte";
  import Projects from "$lib/Projects.svelte";
  import Contact from "$lib/Contact.svelte";
  import Footer from "$lib/Footer.svelte"
</script>


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
