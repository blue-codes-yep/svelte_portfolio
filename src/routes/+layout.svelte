<script>
  import Nav from "$lib/Nav.svelte";
  import Footer from "$lib/Footer.svelte";
  import Particles from "svelte-particles";
  import { loadFull } from "tsparticles";
  import { loadExternalTrailInteraction } from "tsparticles-interaction-external-trail";

  let particlesConfig = {
    particles: {
      number: {
        value: 200,
      },
      size: {
        value: 3,
        random: true,
      },
      opacity: {
        value: 0.5,
        random: true,
        anim: {
          enable: true,
          speed: 2,
          opacity_min: 0.1,
          sync: false,
        },
      },
      twinkle: {
        particles: {
          enable: true,
          frequency: 0.05,
          opacity: 1,
        },
      },
      color: {
        value: "#00BFFF",
      },
    },
    emitters: [
      {
        direction: "none",
        rate: {
          quantity: 1,
          delay: 3,
        },
        size: {
          width: 0,
          height: 0,
        },
        position: {
          x: 50,
          y: 50,
        },
        particles: {
          color: {
            value: "#ffffff",
          },
          links: {
            enable: false,
          },
          move: {
            enable: true,
            speed: 10, // Increased speed to make the trail more noticeable
            direction: "bottom",
            outMode: "out",
            trail: {
                fillColor: "#00BFFF", // Color of the trail
                enable: true, // Enable the trail
                length: 20, // Length of the trail
            },
        },
          number: {
            value: 5,
          },
          opacity: {
            value: 0.5,
          },
          shape: {
            type: "circle",
          },
          size: {
            value: 8,
            random: {
              enable: true,
              minimumValue: 1,
            },
          },
        },
      },
    ],
    interactivity: {
      events: {
        onhover: {
          enable: false,
        },
      },
    },
  };

  let onParticlesLoaded = (event) => {
    const particlesContainer = event.detail.particles;
  };

  let particlesInit = async (engine) => {
    await loadFull(engine);
    await loadExternalTrailInteraction(engine);
  };
</script>

<Particles
  id="tsparticles"
  class="foo bar"
  options={particlesConfig}
  on:particlesLoaded={onParticlesLoaded}
  {particlesInit}
/>

<Nav />
<div class="layoutcontainer">
  <slot />
</div>
<Footer />

<style>
  .layoutcontainer {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    padding: 20px;
    box-sizing: border-box;
    width: 80%;
    margin: 0 auto;
    position: relative;
    z-index: 1;
  }

  .particles-background {
    position: fixed !important;
    top: 0 !important;
    left: 0 !important;
    width: 100% !important;
    height: 100% !important;
    z-index: 0 !important;
    pointer-events: none;
  }
</style>
