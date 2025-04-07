<script lang="ts">
  import { onMount } from 'svelte';

  const socialLinks = [
    { href: 'https://github.com/desk888', icon: 'github', label: 'GitHub' },
    { href: 'https://www.linkedin.com/in/filippinilorenzo/', icon: 'linkedin', label: 'LinkedIn' },
    { href: 'https://twitter.com/https://x.com/lorenzofilipsss', icon: 'twitter', label: 'Twitter' }
  ];

  const words = ['Creative', 'Modern', 'Experienced', 'Professional'];
  let currentIndex = 0;
  let currentWord = words[currentIndex];
  let isAnimating = false;

  function rotateWord() {
    isAnimating = true;
    setTimeout(() => {
      currentIndex = (currentIndex + 1) % words.length;
      currentWord = words[currentIndex];
      isAnimating = false;
    }, 500);
  }

  onMount(async () => {
    setInterval(rotateWord, 3000);
    
    // Initialize particles - using the proper module loading approach for Svelte
    try {
      // Import the required modules
      const { tsParticles } = await import('tsparticles-engine');
      const { loadSlim } = await import('tsparticles-slim');
      
      // Initialize the slim bundle
      await loadSlim(tsParticles);
      
      // Load the particles configuration
      await tsParticles.load('particles', {
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
  .word-rotate {
    display: inline-block;
  }
  
  .word-rotate.animate-out {
    animation: rotateOut 1s ease-in-out;
  }
  
  @keyframes rotateOut {
    0% {
      transform: translateY(0) rotateX(0);
      opacity: 1;
    }
    50% {
      transform: translateY(20px) rotateX(-90deg);
      opacity: 0;
    }
    51% {
      transform: translateY(-20px) rotateX(90deg);
      opacity: 0;
    }
    100% {
      transform: translateY(0) rotateX(0);
      opacity: 1;
    }
  }

  #particles {
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

<section class="min-h-screen relative overflow-hidden bg-gradient-to-br from-emerald-100 via-white to-teal-100">
  <!-- Particles Background -->
  <div id="particles"></div>

  <!-- Background -->
  <div class="absolute inset-0">
    <div class="absolute inset-0 bg-grid-pattern opacity-[0.2]"></div>
  </div>

  <!-- Content -->
  <div class="section-container relative pt-32 pb-20 min-h-screen flex items-center content-wrapper">
    <div class="max-w-3xl">
      <h1 class="text-5xl md:text-6xl font-bold mb-6 animate-slide-up">
        <span class="gradient-text word-rotate" class:animate-out={isAnimating}>{currentWord}</span>
        <br />
        Web & Mobile 
        <br />
        Software Developer 🚀
      </h1>
      
      <p class="text-xl md:text-2xl text-dark/70 mb-12 animate-slide-up" style="animation-delay: 200ms">
        Crafting exceptional full-stack web & mobile experiences through elegant code and thoughtful design.
      </p>

      <div class="flex flex-col sm:flex-row gap-4 animate-slide-up" style="animation-delay: 400ms">
        <a
          href="#projects"
          class="inline-flex items-center justify-center px-8 py-3 bg-primary hover:bg-secondary text-white font-semibold rounded-full transition-colors"
        >
          View My Work
        </a>
        <a
          href="#contact"
          class="inline-flex items-center justify-center px-8 py-3 border-2 border-primary text-primary hover:bg-primary hover:text-white font-semibold rounded-full transition-all"
        >
          Get in Touch
        </a>
      </div>

      <div class="mt-12 flex items-center gap-6 animate-slide-up" style="animation-delay: 600ms">
        {#each socialLinks as link}
          <a
            href={link.href}
            target="_blank"
            rel="noopener noreferrer"
            class="text-dark/50 hover:text-primary transition-colors"
            aria-label={link.label}
          >
            <svg class="w-6 h-6 fill-current">
              <use href={`#icon-${link.icon}`} />
            </svg>
          </a>
        {/each}
      </div>
    </div>
  </div>
</section>

<!-- SVG Icons -->
<svg class="hidden">
  <defs>
    <symbol id="icon-github" viewBox="0 0 24 24">
      <path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z"/>
    </symbol>
    <symbol id="icon-linkedin" viewBox="0 0 24 24">
      <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
    </symbol>
    <symbol id="icon-twitter" viewBox="0 0 24 24">
      <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.17-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
    </symbol>
  </defs>
</svg>