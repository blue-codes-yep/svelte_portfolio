<script lang="ts">
  type Project = {
    title: string;
    description: string;
    technologies: string[];
    github: string;
    demo: string | null;
    details: string;
  };

  const projects: Project[] = [
    {
      title: "AI.AT",
      description: "A collaborative AI project.",
      technologies: ["Python", "Machine Learning"],
      github: "https://github.com/blue-codes-yep/AI.AT",
      demo: null,
      details: "More details about AI.AT project...",
    },
    {
      title: "Cryptid-Refactor",
      description: "A refactoring project.",
      technologies: ["JavaScript", "React"],
      github: "https://github.com/aaroncosmith/Cryptid-Refactor",
      demo: null,
      details: "More details about Cryptid-Refactor project...",
    },
  ];

  let selectedProject: Project | null = null;

  function handleKeyDown(event: KeyboardEvent, project: Project): void {
    // Check if the key pressed is "Enter" or "Space"
    if (event.key === "Enter" || event.key === " ") {
      showDetails(project);
    }
  }

  function showDetails(project: Project): void {
    selectedProject = project;
  }
</script>

<section id="project">
  {#each projects as project}
    <div
      class="project-card"
      on:click={() => showDetails(project)}
      on:keydown={(event) => handleKeyDown(event, project)}
      tabindex="0"
      role="button"
      aria-label="View project details"
    >
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
      {#if selectedProject === project}
        <div class="project-details">
          <h3>{selectedProject.title} Details</h3>
          <p>{selectedProject.details}</p>
        </div>
      {/if}
    </div>
  {/each}
</section>

<style>
  .project-card {
    cursor: pointer;
    border: 1px solid #e0e0e0;
    padding: 20px;
    margin: 15px;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
    width: 300px; /* Set a fixed width for the cards */
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }

  .project-card h2 {
    font-size: 1.2rem;
    margin-bottom: 10px;
  }

  .project-card p {
    font-size: 1rem;
    margin-bottom: 10px;
  }

  .project-card ul {
    list-style: none;
    padding: 0;
    margin-bottom: 10px;
  }

  .project-card li {
    font-size: 0.9rem;
    margin-right: 5px;
    display: inline-block;
  }

  .project-card a {
    font-size: 0.9rem;
    color: #007bff;
    text-decoration: none;
  }

  .project-card:hover {
    transform: scale(1.05);
    box-shadow: 0 6px 8px rgba(0, 0, 0, 0.15);
  }

  .project-details {
    background-color: var(--background-color); 
    color: var(--text-color); 
    border-radius: 8px;
    width: 300px; 
  }
</style>
