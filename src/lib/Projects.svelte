<script lang="ts">
  // Need to focus cards in view, as well as add more containers inside the expanded cards for information
  // Also need to un-expand a card if another is clicked.

  type Project = {
    showDetails: Boolean;
    title: string;
    description: string;
    technologies: string[];
    github: string;
    demo: string | null;
    details: string;
    image: string | null;
    image2: string | null;
  }; 

  let projects: Project[] = [
    {
      title: "AI.AT",
      image:
        "68747470733a2f2f692e696d6775722e636f6d2f5538316e71486e2e706e67.png",
      image2: "aiat2.png",
      description: "A collaborative AI project.",
      technologies: ["Python", "Langchain", "Gpt4", "Flask"],
      github: "https://github.com/blue-codes-yep/AI.AT",
      demo: null,
      details: "More details about AI.AT project...",
    },
    {
      title: "Cryptid-Refactor",
      image: "LogOnPage.png",
      image2: null,
      description: "A refactoring project.",
      technologies: ["JavaScript", "React"],
      github: "https://github.com/aaroncosmith/Cryptid-Refactor",
      demo: null,
      details: "More details about Cryptid-Refactor project...",
    },
    {
      title: "Job Finder",
      image: "jobfinder-jobs.gif",
      image2: null,
      description:
        "An application to help job seekers by streamlining searches.",
      technologies: ["HTML", "CSS", "Node.js", "Express.js", "PostgreSQL"],
      github: "https://github.com/jamariod/JobFinder",
      demo: null,
      details:
        "Member of a 3-person development team building an application...",
    },
    {
      title: "Fire Stocks",
      image: "firestocks.png",
      image2: null,
      description:
        "An application to help job seekers by streamlining searches.",
      technologies: ["HTML", "CSS", "Node.js", "Express.js", "PostgreSQL"],
      github: "https://github.com/jamariod/JobFinder",
      demo: null,
      details:
        "Member of a 3-person development team building an application...",
    },
    {
      title: "24GO",
      image: "24go.png",
      image2: null,
      description:
        "An application to help job seekers by streamlining searches.",
      technologies: ["HTML", "CSS", "Node.js", "Express.js", "PostgreSQL"],
      github: "https://github.com/jamariod/JobFinder",
      demo: null,
      details:
        "Member of a 3-person development team building an application...",
    },
    {
      title: "Steam Market Analysis - AI",
      image: null,
      image2: null,
      description:
        "An application to help job seekers by streamlining searches.",
      technologies: ["HTML", "CSS", "Node.js", "Express.js", "PostgreSQL"],
      github: "https://github.com/jamariod/JobFinder",
      demo: null,
      details:
        "Member of a 3-person development team building an application...",
    },
  ].map((project) => ({ ...project, showDetails: false }));

  let selectedProject: Project | null = null; // No project is selected initially

  function handleKeyDown(event: KeyboardEvent, project: Project): void {
    if (event.key === "Enter" || event.key === " ") {
      showDetails(project);
    }
  }

  function showDetails(project: Project): void {
    const updatedProject = { ...project, showDetails: !project.showDetails };
    const projectIndex = projects.findIndex((p) => p.title === project.title);
    projects[projectIndex] = updatedProject;
    projects = [...projects]; // Trigger Svelte reactivity
    selectedProject =
      selectedProject === updatedProject ? null : updatedProject;
  }
</script>

<section id="project" class="project-grid">
  {#each projects as project}
    <div
      class="project-card {project.showDetails ? 'expanded' : ''}"
      on:click={() => showDetails(project)}
      on:keydown={(event) => handleKeyDown(event, project)}
      tabindex="0"
      role="button"
      aria-label="View project details"
    >
      <h2>{project.title}</h2>
      <div class="image-container">
        <img
          src={project.image}
          alt={project.title}
          class={!project.showDetails ? "active" : ""}
        />
      </div>

      {#if project.showDetails && selectedProject}
      <div class="info-container">
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
          <h3>{project.title} Details</h3>
          <p>{project.details}</p>
        </div>
      </div>
      {/if}
    </div>
  {/each}
</section>

<style>
  /* Grid Layout */
  .project-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-auto-rows: minmax(250px, auto);
    grid-gap: 20px;
  }

  /* Project Card Base Styles */
  .project-card {
    display: flex;
    position: relative;
    flex-direction: column;
    align-items: flex-start;
    cursor: pointer;
    border: 2px solid var(--border-color);
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
    width: 400px;
    flex: 1 0 calc(33.333% - 20px);
    overflow: hidden;
    order: 0;
  }

  /* Image Styles */
  .project-card img {
    max-width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .project-card img.active {
    display: block;
  }

  .project-card.expanded img.active {
    height: 80%;
    width: 80%;
  }

  /* Image Container */
  .image-container {
    height: 350px;
    width: 100%;
    position: relative;
    overflow: hidden;
  }

  /* Expanded Project Card Styles */
  .project-card.expanded {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    height: 100vh;
    width: 100vw;
    overflow: auto;
    max-width: 100%;
    box-sizing: border-box;
    max-height: 100%;
    z-index: 1;
    grid-row-start: 1;
    grid-column: 1 / -1;
  }

  .project-card.expanded .image-container {
  height: auto;
  width: auto;
}

.project-card.expanded .info-container {
  flex: 1; /* Takes up 1 portion of the available space */
  padding: 20px;
}


.project-card.expanded img {
  height: auto;
  width: 100%;
  object-fit: contain;
}


  /* Text and Link Styles */
  .project-card h2,
  .project-card p,
  .project-card ul,
  .project-card li,
  .project-card a {
    font-size: 1rem;
  }

  .project-card h2 {
    position: absolute;
    top: -18px;
    left: 0px;
    color: #fff;
    background: rgba(0, 0, 0, 0.4);
    padding: 4px;
    z-index: 1;
  }

  .project-card p {
    margin-bottom: 10px;
  }

  .project-card ul {
    list-style: none;
    padding: 0;
    margin-bottom: 10px;
  }

  .project-card li {
    margin-right: 5px;
    display: inline-block;
  }

  .project-card a {
    color: #007bff;
    text-decoration: none;
  }

  /* Hover Effect */
  .project-card:hover {
    transform: scale(1.05);
    box-shadow: 0 6px 8px rgba(0, 0, 0, 0.15);
  }

  /* Project Details */
  .project-details {
    background-color: var(--background-color);
    color: var(--text-color);
    border-radius: 8px;
    max-height: 200px;
    width: 300px;
    top: 0;
    left: 0;
  }

  /* Responsive Styles */
  @media (max-width: 768px) {
    .project-grid {
      grid-template-columns: repeat(2, 1fr); /* Change to 2 columns */
    }

    .project-card {
      width: 40vw; /* Adjust width */
    }

    .image-container {
      height: 300px;
    }
  }

  @media (max-width: 480px) {
    .project-grid {
      grid-template-columns: 1fr; /* Single column layout */
    }

    .project-card {
      max-width: 100%;
      box-sizing: border-box;
    }
  }
</style>
