<script lang="ts">
  type Project = {
    showDetails: any;
    title: string;
    description: string;
    technologies: string[];
    github: string;
    demo: string | null;
    details: string;
    image: string | null;
  };

  const projects: Project[] = [
    {
      title: "AI.AT",
      image:
        "68747470733a2f2f692e696d6775722e636f6d2f5538316e71486e2e706e67.png",
      description: "A collaborative AI project.",
      technologies: ["Python", "Langchain", "Gpt4", "Flask"],
      github: "https://github.com/blue-codes-yep/AI.AT",
      demo: null,
      details: "More details about AI.AT project...",
    },
    {
      title: "Cryptid-Refactor",
      image: null,
      description: "A refactoring project.",
      technologies: ["JavaScript", "React"],
      github: "https://github.com/aaroncosmith/Cryptid-Refactor",
      demo: null,
      details: "More details about Cryptid-Refactor project...",
    },
    {
      title: "Job Finder",
      image: null,
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
      image: null,
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
    const projectCards = document.querySelectorAll(".project-card");

    // Reset the expanded class for all cards
    projectCards.forEach((card) => card.classList.remove("expanded"));

    // Apply the expanded class to the clicked card if selected
    if (selectedProject) {
      const clickedCard = document.querySelector(
        `.project-card[data-title="${selectedProject.title}"]`
      ) as HTMLElement;
      if (clickedCard) {
        clickedCard.classList.add("expanded");
      }
    }
  }
</script>

<section id="project" class="project-grid">
  {#each projects as project}
    <div
      class="project-card {project.showDetails ? 'expanded' : ''}"
      data-title={project.title}
      on:click={() => showDetails(project)}
      on:keydown={(event) => handleKeyDown(event, project)}
      tabindex="0"
      role="button"
      aria-label="View project details"
    >
      <h2>{project.title}</h2>
      <div class="image-container">
        <img src={project.image} alt={project.title} />
      </div>
      {#if project.showDetails && selectedProject}
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
    grid-auto-rows: minmax(250px, auto); /* Adjust the row height as needed */
    grid-gap: 20px;
  }

  .project-card {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    cursor: pointer;
    border: 2px solid var(--border-color);
    padding: 15px;
    margin: 10px;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
    width: 400px;
    position: relative;
    flex: 0 0 calc(33.333% - 20px);
    transition: max-height 0.3s ease;
    overflow: hidden;
  }

  .project-card img {
    max-width: 100%;
    height: 100%;
    display: block;
    position: absolute;
    object-fit: cover;
  }

  .image-container {
  height: 250px; /* Set a fixed height */
  width: 100%;
  position: relative;
  overflow: hidden; /* Add this line */
}

.project-card.expanded {
  /* Adjust the styles as needed for the expanded state */
  flex: 1 1 50%;
  grid-row-end: span 2;
  overflow: auto; /* Add this line to enable scrolling for additional content */
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
