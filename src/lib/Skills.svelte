<script lang="ts">
  const skills = [
    {
      category: 'Frontend Development',
      icon: '🎨',
      items: [
        { name: 'React/Next.js', level: 100 },
        { name: 'Vue', level: 50 },
        { name: 'Svelte/SvelteKit', level: 50 },
        { name: 'TypeScript', level: 92 },
        { name: 'Tailwind CSS', level: 88 }
      ]
    },
    {
      category: 'Backend Development',
      icon: '⚙️',
      items: [
        { name: 'Go/Golang', level: 90 },
        { name: 'Python/Django', level: 85 },
        { name: 'PostgreSQL/MySQL/MongoDB', level: 88 },
        { name: 'Microservices', level: 82 },
        { name: 'REST APIs / GraphQL / gRPC', level: 95 }
      ]
    },
    {
      category: 'DevOps & Tools',
      icon: '🛠️',
      items: [
        { name: 'Docker', level: 85 },
        { name: 'AWS', level: 80 },
        { name: 'CI/CD', level: 88 },
        { name: 'Git', level: 92 },
        { name: 'Testing', level: 85 }
      ]
    }
  ];
</script>

<section id="skills" class="py-24 bg-white">
  <div class="section-container">
    <div class="text-center mb-16">
      <h2 class="text-4xl md:text-5xl font-bold mb-4">Skills & Expertise</h2>
      <p class="text-xl text-dark/70 max-w-2xl mx-auto">
        A comprehensive overview of my technical skills and proficiency levels.
      </p>
    </div>

    <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
      {#each skills as { category, icon, items }}
        <div class="card p-8">
          <div class="flex items-center gap-3 mb-8">
            <span class="text-3xl">{icon}</span>
            <h3 class="text-xl font-semibold">{category}</h3>
          </div>
          <div class="space-y-6">
            {#each items as { name, level }}
              <div>
                <div class="flex justify-between mb-2">
                  <span class="font-medium">{name}</span>
                </div>
                <div class="h-2 bg-gray-200 rounded-full overflow-hidden">
                  <div
                    class="h-full bg-gradient-to-r from-primary to-secondary rounded-full transition-all duration-500"
                    style="width: {level}%"
                  ></div>
                </div>
              </div>
            {/each}
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>