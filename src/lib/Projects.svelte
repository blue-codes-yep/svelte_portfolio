<script lang="ts">
  import * as animateScroll from "svelte-scrollto";

  type Technology = {
    name: string;
    image: string | null;
  };

  type Project = {
    showDetails: Boolean;
    title: string;
    description: string;
    technologies: Technology[];
    github: string;
    demo: string | null;
    details: string;
    image: string | null;
    image2: string | null;
  };

  let projects: Project[] = [
    {
      title: "AI Video-Genteration",
      image:
        "68747470733a2f2f692e696d6775722e636f6d2f5538316e71486e2e706e67.png",
      image2: "aiat2.png",
      description:
        "Solo project consisting of a video generation web application that uses a large language model (LLM) to produce a voiced-over video with imagery and words based on the user's chosen topic input. Learned from and overcame challenges with the project specifically related to working with the LLM around prompting, and maintaining response context between prompts for topic script output. Also faced and met user interface challenges related to display of progress.",
      technologies: [
        { name: "Python", image: "/python.png" },
        { name: "Javascript", image: "/js.png" },
        { name: "Gpt4", image: "/gpt4.png" },
        { name: "Flask", image: "/flask.png" },
      ],
      github: "https://github.com/blue-codes-yep/AI.AT",
      demo: null,
      details:
        "Related technologies: Python, Flask, Base64, IO, Boto3, spaCy, Langchain, numpy, PIL, moviepy, pydub, celery, Javascript, React & Material UI",
    },
    {
      title: "Freelance Livestream App",
      image: null,
      image2: null,
      description:
        "An application to help job seekers by streamlining searches.",
      technologies: [
        { name: "Python", image: "/python.png" },
        { name: "Javascript", image: "/js.png" },
        { name: "Gpt4", image: "/gpt4.png" },
        { name: "Flask", image: "/flask.png" },
      ],
      github: "https://github.com/jamariod/JobFinder",
      demo: null,
      details:
        "Member of a 3-person development team building an application...",
    },
    {
      title: "Cryptid-Refactor",
      image: "LogOnPage.png",
      image2: null,
      description: "A refactoring project.",
      technologies: [
        { name: "Python", image: "/python.png" },
        { name: "Javascript", image: "/js.png" },
        { name: "Gpt4", image: "/gpt4.png" },
        { name: "Flask", image: "/flask.png" },
      ],
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
      technologies: [
        { name: "Python", image: "/python.png" },
        { name: "Javascript", image: "/js.png" },
        { name: "Gpt4", image: "/gpt4.png" },
        { name: "Flask", image: "/flask.png" },
      ],
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
      technologies: [
        { name: "Python", image: "/python.png" },
        { name: "Javascript", image: "/js.png" },
        { name: "Gpt4", image: "/gpt4.png" },
        { name: "Flask", image: "/flask.png" },
      ],
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
      technologies: [
        { name: "Python", image: "/python.png" },
        { name: "Javascript", image: "/js.png" },
        { name: "Gpt4", image: "/gpt4.png" },
        { name: "Flask", image: "/flask.png" },
      ],
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
      technologies: [
        { name: "Python", image: "/python.png" },
        { name: "Javascript", image: "/js.png" },
        { name: "Gpt4", image: "/gpt4.png" },
        { name: "Flask", image: "/flask.png" },
      ],
      github: "https://github.com/jamariod/JobFinder",
      demo: null,
      details:
        "Member of a 3-person development team building an application...",
    },
    {
      title: "Amazon Price Tracker",
      image: null,
      image2: null,
      description:
        "Scrapes urls given in the trackers csv file. Will give price, title, review count, if in stock, and export it to an excel file. Done as practice with beautifulsoup as GPU prices have been dropping, and have been curious to see how they drop over the coming months.You can set a scheduled run of the script for it to run say once a day..etc.",
      technologies: [
        { name: "Python", image: "/python.png" },
        { name: "Javascript", image: "/js.png" },
        { name: "Gpt4", image: "/gpt4.png" },
        { name: "Flask", image: "/flask.png" },
      ],
      github: "https://github.com/jamariod/JobFinder",
      demo: null,
      details:
        "Member of a 3-person development team building an application...",
    },
    {
      title: "Discord Bot",
      image: null,
      image2: null,
      description:
        "Discord bot that currently allows users, to set-roles, check their rank for a game called Valorant, as well as upload custom emojis.",
      technologies: [
        { name: "Python", image: "/python.png" },
        { name: "Javascript", image: "/js.png" },
        { name: "Gpt4", image: "/gpt4.png" },
        { name: "Flask", image: "/flask.png" },
      ],
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
    // Un-expand the previously selected project
    if (selectedProject && selectedProject !== project) {
      selectedProject.showDetails = false;
    }

    // Toggle the details for the clicked project
    project.showDetails = !project.showDetails;
    selectedProject = project.showDetails ? project : null;

    // Update the projects array to reflect the changes
    const projectIndex = projects.findIndex((p) => p.title === project.title);
    projects[projectIndex] = project;
    projects = [...projects];


    if (selectedProject) {
    animateScroll.scrollTo({ element: "#projects", duration: 100 });
  } else {
    animateScroll.scrollTo({ element: "#projects", duration: 100 });
  }
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
          <h3>{project.title}</h3>
          <p>{project.description}</p>
          <a href={project.github}>GitHub</a>
          {#if project.demo}
            <a href={project.demo}>Live Demo</a>
          {/if}
          <div class="project-details">
            <p>{project.details}</p>
          </div>
        </div>
        <div class="footer-container">
          {#each project.technologies as tech}
            {#if tech.image}
              <img src={tech.image} alt={tech.name} />
            {/if}
          {/each}
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
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    height: 100vh;
    width: 100vw;
    overflow: auto;
    max-width: 100%;
    max-height: 100%;
    z-index: 1;
    grid-row-start: 1;
    grid-column: 1 / -1;
  }
  .project-card.expanded .info-container,
  .project-card.expanded .image-container {
    flex: none;
  }

  .project-card.expanded .footer-container {
    flex: 1;
    width: 100%;
    padding: 20px;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
  }

  .project-card.expanded .image-container {
    height: auto;
    width: auto;
  }

  .project-card.expanded .info-container {
    flex: 1;
    padding: 20px;
  }

  .project-card.expanded .footer-container {
    flex: 1;
    padding: 20px;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
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

  .footer-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    align-items: center;
  }

  .footer-container img {
    max-width: 100px;
    max-height: 100px;
    margin-right: 10px;
  }
  /* Responsive Styles */
  @media (max-width: 768px) {
    .project-grid {
      grid-template-columns: repeat(2, 1fr); 
    }

    .project-card {
      width: 40vw; 
    }

    .image-container {
      height: 300px;
    }
  }

  @media (max-width: 480px) {
    .project-grid {
      grid-template-columns: 1fr; 
    }

    .project-card {
      max-width: 100%;
      box-sizing: border-box;
    }
  }
</style>