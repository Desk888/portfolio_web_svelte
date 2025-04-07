<script lang="ts">
  import { onMount } from 'svelte';

  let isScrolled = false;
  let isMenuOpen = false;

  const navItems = [
    { href: '#', text: 'Home' },
    { href: '#about', text: 'About' },
    { href: '#projects', text: 'Projects' },
    { href: '#skills', text: 'Skills' },
    { href: '#contact', text: 'Contact' }
  ];

  onMount(() => {
    const handleScroll = () => {
      isScrolled = window.scrollY > 20;
    };
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  });
</script>

<header class="fixed top-0 left-0 right-0 z-50 transition-all duration-300"
  class:bg-white={isScrolled}
  class:shadow-lg={isScrolled}
  class:bg-transparent={!isScrolled}>
  <nav class="section-container">
    <div class="flex items-center justify-between h-16 md:h-20 relative">
      <!-- Logo -->
      <a href="/" class="flex items-center">
        <div class="w-12 h-12 bg-primary rounded-full flex items-center justify-center">
          <svg class="w-7 h-7 text-white" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
            <path d="M16 18L22 12L16 6" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M8 6L2 12L8 18" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </div>
      </a>

      <!-- Desktop menu -->
      <ul class="hidden md:flex space-x-8">
        {#each navItems as item}
          <li>
            <a
              href={item.href}
              class="text-dark/70 hover:text-primary font-medium transition-colors relative after:absolute after:bottom-0 after:left-0 after:w-full after:h-0.5 after:bg-primary after:scale-x-0 hover:after:scale-x-100 after:transition-transform after:duration-300 after:origin-left pb-1"
            >
              {item.text}
            </a>
          </li>
        {/each}
      </ul>

      <!-- Mobile menu button -->
      <button
        class="md:hidden p-2 rounded-lg hover:bg-gray-100"
        on:click={() => isMenuOpen = !isMenuOpen}
        aria-label="Toggle menu">
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          {#if isMenuOpen}
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
          {:else}
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
          {/if}
        </svg>
      </button>
    </div>

    <!-- Mobile menu -->
    {#if isMenuOpen}
      <div class="md:hidden bg-white shadow-lg rounded-b-2xl animate-fade-in">
        <ul class="py-2">
          {#each navItems as item}
            <li>
              <a
                href={item.href}
                class="block px-4 py-2 text-dark/70 hover:bg-gray-50 hover:text-primary relative after:absolute after:bottom-0 after:left-4 after:right-4 after:h-0.5 after:bg-primary after:scale-x-0 hover:after:scale-x-100 after:transition-transform after:duration-300 after:origin-left"
                on:click={() => isMenuOpen = false}
              >
                {item.text}
              </a>
            </li>
          {/each}
        </ul>
      </div>
    {/if}
  </nav>
  <!-- Dividing line -->
  <div class="h-[1px] bg-slate-200"></div>
</header>