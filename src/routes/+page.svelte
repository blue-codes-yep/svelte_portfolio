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
  width: 80%;
  margin: 0 auto;
  padding: 20px;
  box-sizing: border-box;
}

.main-section {
  width: 100%;

  margin-bottom: 40px;
  box-sizing: border-box;
}

#about-me {
  padding: 80px;
  border: 2px solid var(--border-color);
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  background-color: var(--section-background-color);
  transition: all 0.3s ease;
}

#about-me:hover {
  transform: scale(1.02);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
}


</style>
