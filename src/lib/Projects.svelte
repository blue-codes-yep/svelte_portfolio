<script>
  const projects = [
    {
      title: "AI.AT",
      description: "A collaborative AI project.",
      technologies: ["Python", "Machine Learning"],
      github: "https://github.com/blue-codes-yep/AI.AT",
      demo: null
    },
    {
      title: "Cryptid-Refactor",
      description: "A refactoring project.",
      technologies: ["JavaScript", "React"],
      github: "https://github.com/aaroncosmith/Cryptid-Refactor",
      demo: null
    }
  ];
</script>

<section id="project">
  {#each projects as project}
    <div class="project-card">
      <h2>{project.title}</h2>
      <p>{project.description}</p>
      <ul>
        {#each project.technologies as tech}
          <li>{tech}</li>
        {/each}
      </ul>
      <a href={project.github}>GitHub</a>
      {#if project.demo}
        <a href={project.demo}>Live Demo</a>
      {/if}
    </div>
  {/each}
</section>

<style>
  .project-card {
    /* Styling for the project cards */
  }
</style>
