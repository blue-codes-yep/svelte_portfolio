<script lang="ts">
  import Nav from "$lib/Nav.svelte";
  import Footer from "$lib/Footer.svelte";
  import Particles from "svelte-particles";
  import { loadFull } from "tsparticles";
  import type { Particle } from "tsparticles-engine/types/Core/Particle"; // Import the Particle type

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
          delay: 35,
        },
        size: {
          width: 0,
          height: 0,
        },
        position: {
          x: 50,
          y: 250,
        },
        particles: {
          color: {
            value: "#737373",
          },
          links: {
            enable: false,
          },
          move: {
            enable: true,
            speed: 7,
            direction: "bottom",
            outMode: "out",
          },
          number: {
            value: 2,
          },
          opacity: {
            value: 0.9,
          },
          shape: {
            type: "circle",
          },
          size: {
            value: 3,
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

  let particlesCanvas: HTMLCanvasElement;
  let particlesArray: Particle[] = [];

  let onParticlesLoaded = (event: CustomEvent) => {
    const particlesContainer = event.detail.particles;
    particlesCanvas = particlesContainer.canvas.element;

    if (particlesContainer.particles && particlesContainer.particles._array) {
      particlesArray = particlesContainer.particles._array;
    }

    if (particlesArray) {
      console.log("Particles Loaded:", particlesArray.length);
    } else {
      console.log("Particles array is undefined");
    }

    if (particlesArray && particlesArray.length > 0) {
      drawTrails();
    }
  };

  const emitterTrails = new Map<
    number,
    { x: number; y: number; timestamp: number }[]
  >();

  const distance = (x1: number, y1: number, x2: number, y2: number) => {
    return Math.sqrt(Math.pow(x2 - x1, 2) + Math.pow(y2 - y1, 2));
  };

  const drawTrails = () => {
    const ctx = particlesCanvas.getContext("2d");
    if (!ctx) {
      console.log("Context is null");
      return;
    }

    const isEmitterParticle = (particle: Particle, index: number) =>
      index >= 200;

    particlesArray.forEach((particle: Particle, index: number) => {
      if (isEmitterParticle(particle, index)) {
        let trails = emitterTrails.get(particle.id);
        if (!trails) {
          trails = [];
          emitterTrails.set(particle.id, trails);
        }

        trails.push({
          x: particle.position.x,
          y: particle.position.y,
          timestamp: Date.now(),
        });

        const currentTime = Date.now();
        const trailDuration = 2500; 
        while (
          trails.length > 0 &&
          currentTime - trails[0].timestamp > trailDuration
        ) {
          trails.shift();
        }

      // Limit the number of trail points
      const maxTrailPoints = 1500; 
      if (trails.length > maxTrailPoints) {
        trails.shift();
      }

        for (let i = 1; i < trails.length; i++) {
          const start = trails[i - 1];
          const end = trails[i];
          const ageStart = (currentTime - start.timestamp) / 2000;
          const ageEnd = (currentTime - end.timestamp) / 2000;

          // Check if the particle has likely wrapped around the screen
          if (distance(start.x, start.y, end.x, end.y) < 100) {
            const gradient = ctx.createLinearGradient(
              start.x,
              start.y,
              end.x,
              end.y
            );
            gradient.addColorStop(0, `rgba(97, 102, 125, ${.05 - ageStart})`);

            gradient.addColorStop(1, `rgba(97, 102, 125, ${.75 - ageEnd})`);

            ctx.beginPath();
            ctx.moveTo(start.x, start.y);
            ctx.lineTo(end.x, end.y);
            ctx.strokeStyle = gradient;
            ctx.lineWidth = 3;
            ctx.stroke();
            ctx.closePath();
          }
        }
      }
    });
    requestAnimationFrame(drawTrails);
  };
  let particlesInit = async (engine: any) => {
    await loadFull(engine);
  };
</script>

<Particles
  id="tsparticles"
  class="particles-background"
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
