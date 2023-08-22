<script lang="ts">
  type Project = {
    showDetails: any;
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
    {
      title: "Job Finder",
      description:
        "An application to help job seekers by streamlining searches.",
      technologies: ["HTML", "CSS", "Node.js", "Express.js", "PostgreSQL"],
      github: "https://github.com/jamariod/JobFinder",
      demo: null,
      details:
        "Member of a 3-person development team building an application...",
    },
    {
      title: "PP(Project Placeholder)",
      description:
        "An application to help job seekers by streamlining searches.",
      technologies: ["HTML", "CSS", "Node.js", "Express.js", "PostgreSQL"],
      github: "https://github.com/jamariod/JobFinder",
      demo: null,
      details:
        "Member of a 3-person development team building an application...",
    },
  ].map((project) => ({ ...project, showDetails: false }));

  let selectedProject: Project | null = null;

  function handleKeyDown(event: KeyboardEvent, project: Project): void {
    if (event.key === "Enter" || event.key === " ") {
      showDetails(project);
    }
  }

  function showDetails(project: Project): void {
  project.showDetails = !project.showDetails;
  selectedProject = selectedProject === project ? null : project;

  // Query all project cards
  const projectCards = document.querySelectorAll('.project-card');

  // Reset the expanded class for all cards
  projectCards.forEach((card) => card.classList.remove('expanded'));

  // Apply the expanded class to the clicked card if selected
  if (selectedProject) {
    const clickedCard = document.querySelector(`.project-card[data-title="${selectedProject.title}"]`) as HTMLElement;
    if (clickedCard) {
      clickedCard.classList.add('expanded');
    }
  }
}

</script>

<section id="project" class="project-grid">
  {#each projects as project}
    <div
      class="project-card {project.showDetails ? 'expanded' : ''}"
      data-title="{project.title}"
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
  .project-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-auto-rows: 250px; /* Base height of the card */
    grid-gap: 20px;
  }

  .project-card {
    cursor: pointer;
    border: 2px solid var(--border-color);
    padding: 15px;
    margin: 0 auto;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
    width: 300px;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    position: relative;
    flex: 1 0 calc(25% - 30px);
    transition: max-height 0.3s ease;
  }

  .project-card.expanded {
    grid-row-end: span 2; /* Span two rows when expanded */
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
    max-height: 200px;
    width: 300px;
    top: 0;
    left: 0;
    overflow: auto;
  }
</style>
