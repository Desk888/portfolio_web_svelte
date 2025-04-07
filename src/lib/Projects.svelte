<script lang="ts">
  import { onMount } from 'svelte';
  
  const projects = [
    {
      title: 'HyperScriber AI',
      description: 'Performance-focused and AI-Powered Content Agency for SaaS Startups.',
      image: 'https://portfolio-website-assets-cdn.s3.eu-west-2.amazonaws.com/hyperscriber_banner.png',
      tags: ['React', 'Tailwind CSS', 'TypeScript'],
      link: 'https://hyperscriber.com/'
    },
    {
      title: 'Social Stoic',
      description: 'Social Stoic is a company offering dating coaching programs for men worldwide.',
      image: 'https://portfolio-website-assets-cdn.s3.eu-west-2.amazonaws.com/socialstoic_banner.png',
      tags: ['React', 'Tailwind CSS', 'TypeScript'],
      link: 'https://socialstoic.com/'
    },
    {
      title: 'MoodyTube',
      description: 'A comprehensive YouTube sentiment analysis tool for video creators.',
      image: 'https://images.unsplash.com/photo-1615525137689-198778541af6?q=80&w=1932&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
      tags: ['Python', 'PostgreSQL', 'Google Cloud'],
      link: 'https://github.com/Desk888/moodytube-youtube-tool'
    }
  ];

  onMount(async () => {
    try {
      // Import the required modules
      const { tsParticles } = await import('tsparticles-engine');
      const { loadSlim } = await import('tsparticles-slim');
      
      // Initialize the slim bundle
      await loadSlim(tsParticles);
      
      // Load the particles configuration
      await tsParticles.load('projects-particles', {
        fullScreen: { enable: false },
        fpsLimit: 60,
        particles: {
          number: {
            value: 40,
            density: {
              enable: true,
              value_area: 900
            }
          },
          color: {
            value: ["#10b981", "#059669", "#d1fae5"]
          },
          shape: {
            type: "circle"
          },
          opacity: {
            value: 0.4,
            random: true,
            anim: {
              enable: true,
              speed: 0.8,
              opacity_min: 0.1,
              sync: false
            }
          },
          size: {
            value: 2.5,
            random: true,
            anim: {
              enable: true,
              speed: 1.5,
              size_min: 0.2,
              sync: false
            }
          },
          links: {
            enable: true,
            distance: 150,
            color: "#10b981",
            opacity: 0.3,
            width: 1
          },
          move: {
            enable: true,
            speed: 0.8,
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
                opacity: 0.8
              }
            },
            push: {
              quantity: 3
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
  .card {
    background-color: rgba(255, 255, 255, 0.85);
    backdrop-filter: blur(5px);
    border-radius: 0.5rem;
    overflow: hidden;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.05);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }
  
  .card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  }
  
  #projects-particles {
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

<section id="projects" class="py-24 bg-gradient-to-br from-emerald-100 via-white to-teal-100 relative">
  <!-- Particles Background -->
  <div id="projects-particles"></div>
  
  <div class="section-container content-wrapper">
    <div class="text-center mb-16">
      <h2 class="text-4xl md:text-5xl font-bold mb-4">Featured Projects</h2>
      <p class="text-xl text-dark/70 max-w-2xl mx-auto">
        Explore some of my recent work that showcases my expertise in full-stack development.
      </p>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
      {#each projects as project}
        <article class="card group">
          <div class="relative h-48 overflow-hidden">
            <img
              src={project.image}
              alt={project.title}
              class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
            />
          </div>
          <div class="p-6">
            <h3 class="text-xl font-semibold mb-2">{project.title}</h3>
            <p class="text-dark/70 mb-4">{project.description}</p>
            <div class="flex flex-wrap gap-2 mb-6">
              {#each project.tags as tag}
                <span class="px-3 py-1 bg-primary/10 text-primary rounded-full text-sm">
                  {tag}
                </span>
              {/each}
            </div>
            <a
              href={project.link}
              class="inline-flex items-center text-primary hover:text-secondary font-medium transition-colors"
            >
              View Project
              <svg class="w-4 h-4 ml-2" viewBox="0 0 24 24" fill="none" stroke="currentColor">
                <path d="M5 12h14m-7-7l7 7-7 7" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
            </a>
          </div>
        </article>
      {/each}
    </div>
  </div>
</section>