<script lang="ts">
  import { onMount } from 'svelte';

  onMount(async () => {
    // Initialize particles - using the proper module loading approach for Svelte
    try {
      // Import the required modules
      const { tsParticles } = await import('tsparticles-engine');
      const { loadSlim } = await import('tsparticles-slim');
      
      // Initialize the slim bundle
      await loadSlim(tsParticles);
      
      // Load the particles configuration
      await tsParticles.load('contact-particles', {
        fullScreen: { enable: false },
        fpsLimit: 60,
        particles: {
          number: {
            value: 80,
            density: {
              enable: true,
              value_area: 800
            }
          },
          color: {
            value: ["#10b981", "#059669", "#d1fae5"]
          },
          shape: {
            type: "circle"
          },
          opacity: {
            value: 0.5,
            random: true,
            anim: {
              enable: true,
              speed: 1,
              opacity_min: 0.1,
              sync: false
            }
          },
          size: {
            value: 3,
            random: true,
            anim: {
              enable: true,
              speed: 2,
              size_min: 0.3,
              sync: false
            }
          },
          links: {
            enable: true,
            distance: 150,
            color: "#10b981",
            opacity: 0.4,
            width: 1
          },
          move: {
            enable: true,
            speed: 1,
            direction: "none",
            random: false,
            straight: false,
            outModes: "out",
            attract: {
              enable: false,
              rotateX: 600,
              rotateY: 1200
            }
          }
        },
        interactivity: {
          detectsOn: "canvas",
          events: {
            onHover: {
              enable: true,
              mode: "grab"
            },
            onClick: {
              enable: true,
              mode: "push"
            },
            resize: true
          },
          modes: {
            grab: {
              distance: 140,
              links: {
                opacity: 1
              }
            },
            push: {
              quantity: 4
            }
          }
        },
        detectRetina: true
      });
    } catch (error) {
      console.error("Failed to load particles:", error);
    }
  });
</script>

<style>
  #contact-particles {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    z-index: 1;
  }

  .content-wrapper {
    position: relative;
    z-index: 2;
  }
</style>

<section id="contact" class="py-24 bg-gradient-to-br from-emerald-100 via-white to-teal-100 relative overflow-hidden">
  <!-- Particles Background -->
  <div id="contact-particles"></div>

  <!-- Content -->
  <div class="section-container max-w-4xl content-wrapper">
    <div class="text-center mb-16">
      <h2 class="text-4xl md:text-5xl font-bold mb-4">Let's Connect</h2>
      <p class="text-xl text-dark/70">
        Interested in working together? Let's discuss your project and bring your ideas to life.
      </p>
      <p class="text-lg text-primary mt-2">
        work.lorenzofilippini@gmail.com
      </p>
    </div>

    <div class="flex justify-center">
      <a
        href="mailto:work.lorenzofilippini@gmail.com?subject=Let's%20Connect&body=Hi%2C%20I'm%20interested%20in%20working%20together%20on%20a%20project."
        class="px-8 py-3 bg-primary hover:bg-secondary text-white font-semibold rounded-full transition-colors inline-block"
      >
        Send Message
      </a>
    </div>
  </div>
</section>