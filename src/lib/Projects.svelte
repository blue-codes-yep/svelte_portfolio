<script lang="ts">
  $: if (projects) {
    projects.forEach((project) => {
      if (project.customClass) {
        console.log(`customClass for ${project.title}: ${project.customClass}`);
      }
    });
  }
  import * as animateScroll from "svelte-scrollto";

  type Technology = {
    name: string;
    image: string | null;
  };

  type Project = {
    customClass?: string;
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
        { name: "Flask", image: "/flask.png" },
        { name: "Javascript", image: "/js.png" },
        { name: "🦜🔗 LangChain", image: "/langchain.png" },
        { name: "React", image: "/react.png" },
        { name: "Material UI", image: "/materialui.png" },
        { name: "Gpt4", image: "/gpt4.png" },
      ],
      github: "https://github.com/blue-codes-yep/AI.AT",
      demo: null,
      details:
        "Related technologies: Python, Flask, Base64, IO, Boto3, spaCy, Langchain, numpy, PIL, moviepy, pydub, celery, Javascript, React & Material UI",
    },
    {
      title: "Freelance Livestream App",
      image: "landing.png",
      image2: "live.png",
      description:
        "Solo freelance project built for an Upwork client. That provides a live-streaming experience using Zoom's SDK. To connect users with the given information, to connect, chat, and video call all within zoom's environment within the customers website.",
      technologies: [{ name: "Javascript", image: "/js.png" }],
      github: "https://github.com/jamariod/JobFinder",
      demo: "https://sexscotchandcigarslive.com/",
      details:
        "Built using Zoom SDK, React, HTML & CSS. Used Amazon Web Services and NGINX for backend. Overcame design and user interface challenges with animation and styles",
    },
    {
      title: "Cryptid-Refactor",
      image: "LogOnPage.png",
      image2: null,
      description:
        "Cryptid-Refactor is a 3-person team project that aims to provide a secure and anonymous chat messaging experience. The application allows users to create chat rooms that are password-protected (hashed by bcrypt) and share the password with friends. The project uses socket.io for real-time messaging and does not store any chat information. The application was initially started in NEXT.js but was later refactored to Create React App due to challenges with global state and CSS rendering. The project has overcome several challenges, including the addition of multiple channels and password-protected chats.",
      technologies: [{ name: "Javascript", image: "/js.png" }],
      github: "https://github.com/aaroncosmith/Cryptid-Refactor",
      demo: null,
      details:
        "Related Tech: Frontend: Javascript,React, StyledComponents Backend: Node.js, Express, Socket.io, PostgreSQL, Notable Node Modules: bcrypt, dotenv, express-session, pg-promise, socket.io-client",
    },
    {
      title: "Job Finder",
      image: "jobfinder-jobs.gif",
      image2: null,
      description:
        "Team project developed during a 1-week sprint as part of a coding bootcamp. JobFinder is a web application designed to streamline the job search process for users. It allows users to register and login, view recent developer job listings, and search for jobs based on various parameters. The project overcame challenges related to user authentication and job data scraping, and it features a user-friendly interface with Bootstrap.",
      technologies: [{ name: "Javascript", image: "/js.png" }],
      github: "https://github.com/jamariod/JobFinder",
      demo: null,
      details:
        "Related Tech: Front-End: HTML, CSS, Bootstrap, JavaScript, Back-End: Node.js, Express, PostgreSQL, Notable Node Modules: axios, bcrypt, cheerio, dotenv, ejs, express-session, pg-promise, puppeteer",
    },
    {
      title: "Fire Stocks",
      image: "firestocks.png",
      image2: null,
      description:
        "Solo developed Python application that uses spaCy for NLP, pandas for data manipulation, yfinance for fetching stock data, and streamlit for the UI. It allows users to add RSS links for stock news and displays various stock metrics in a DataFrame. The application also practices with BeautifulSoup for web scraping.",
      technologies: [{ name: "Python", image: "/python.png" }],
      github: "https://github.com/jamariod/JobFinder",
      demo: null,
      details:
        "Related Tech: Python, spaCy, pandas, yfinance, streamlit, BeautifulSoup",
    },
    {
      title: "24GO",
      image: "24go.png",
      image2: null,
      description:
        "Member of a 3-person development, this project is a front-end web application built with JavaScript, HTML, and CSS. It uses multiple APIs to aggregate events like sports, music, and comedy based on the user's location. The application also provides weather information and links to Wikipedia pages for nearby cultural or historic sites.",
      technologies: [{ name: "Javascript", image: "/js.png" }],
      github: "https://github.com/jamariod/JobFinder",
      demo: null,
      details:
        "Related Tech: JavaScript, HTML, CSS, APIs (eventful, mediawiki, foursquare, weatherapi)",
    },
    {
      title: "Steam Market Analysis - AI",
      customClass: "steam-market",
      image: "marketprediction.png",
      image2: null,
      description:
        "Solo project focused on creating an AI-based Steam Market Analyzer using Python. The project aims to predict market trends for Steam items by leveraging neural networks. The application is divided into two main parts: data gathering and analysis. The data gathering is done through web scraping techniques, while the analysis is performed using a neural network model built with TensorFlow. The project has undergone several updates to improve data handling and model efficiency, including the addition of more neural network layers.",
      technologies: [{ name: "Python", image: "/python.png" }],
      github: "https://github.com/blue-codes-yep/AI_STEAM",
      demo: null,
      details:
        "Related Tech: Python, TensorFlow, Pandas, Web Scraping (BeautifulSoup)",
    },
    {
      title: "Amazon Price Tracker",
      image: "amzdata.png",
      image2: null,
      description:
        "A Python application designed to scrape GPU prices from Amazon using BeautifulSoup. It targets URLs specified in a CSV file named trackers. The scraper fetches various data points including the product's price, title, review count, and stock availability. This data is then exported to an Excel file for further analysis. It offers the flexibility to schedule runs, allowing for daily or periodic data collection.",
      technologies: [{ name: "Python", image: "/python.png" }],
      github: "https://github.com/jamariod/JobFinder",
      demo: null,
      details: "Related Tech: Python, BeautifulSoup, Pandas, Requests, Excel",
    },
    {
      title: "Discord Bot",
      customClass: "discord-bot",
      image: "discord.png",
      image2: null,
      description:
        "Discord bot that currently allows users, to set-roles, check their rank for a game called Valorant, as well as upload custom emojis.",
      technologies: [{ name: "Python", image: "/python.png" }],
      github: "https://github.com/jamariod/JobFinder",
      demo: null,
      details:
        "Solo Developed project to accomplish a few tasks I wanted to automate within a Discord server.",
    },
  ].map((project) => ({ ...project, showDetails: false }));

  let selectedProject: Project | null = null;

  function handleKeyDown(event: KeyboardEvent, project: Project): void {
    if (event.key === "Enter" || event.key === " ") {
      showDetails(project);
    }
  }
  function showDetails(project: Project): void {
    if (selectedProject && selectedProject !== project) {
      selectedProject.showDetails = false;
    }

    project.showDetails = !project.showDetails;
    selectedProject = project.showDetails ? project : null;

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
      <div
        class="image-container {project.customClass ? project.customClass : ''}"
      >
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
  /* Custom Classes If Needed */

  /* Project Grid Styles */
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
    height: 100%;
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
    margin-top: 2px;
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
