<script lang="ts">
  const projects = [
    {
      title: 'HyperScriber AI',
      description: 'A modern e-commerce platform built with Next.js, featuring real-time inventory management and seamless payment integration.',
      image: 'https://images.unsplash.com/photo-1454117096348-e4abbeba002c?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
      tags: ['React', 'Tailwind CSS', 'TypeScript'],
      link: '#'
    },
    {
      title: 'Social Stoic',
      description: 'An AI-powered platform that generates high-quality content using advanced language models and machine learning algorithms.',
      image: 'https://images.unsplash.com/photo-1454117096348-e4abbeba002c?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
      tags: ['React', 'Tailwind CSS', 'TypeScript'],
      link: '#'
    },
    {
      title: 'MoodyTube',
      description: 'A comprehensive analytics dashboard providing real-time insights and data visualization for business metrics.',
      image: 'https://images.unsplash.com/photo-1454117096348-e4abbeba002c?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
      tags: ['Python', 'PostgreSQL', 'Google Cloud'],
      link: '#'
    }
  ];
</script>

<section id="projects" class="py-24 bg-white">
  <div class="section-container">
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