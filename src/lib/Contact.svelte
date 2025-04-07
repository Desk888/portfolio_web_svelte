<section id="contact" class="py-24 bg-white">
  <div class="section-container max-w-4xl">
    <div class="text-center mb-16">
      <h2 class="text-4xl md:text-5xl font-bold mb-4">Let's Connect</h2>
      <p class="text-xl text-dark/70">
        Interested in working together? Let's discuss your project and bring your ideas to life.
      </p>
    </div>

    <div class="card p-8 md:p-12">
      <form class="space-y-6">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <div>
            <label for="name" class="block text-sm font-medium text-dark/70 mb-2">Name</label>
            <input
              type="text"
              id="name"
              class="w-full px-4 py-3 rounded-lg border border-gray-200 focus:border-primary focus:ring-2 focus:ring-primary/20 outline-none transition-all"
              placeholder="John Doe"
            />
          </div>
          <div>
            <label for="email" class="block text-sm font-medium text-dark/70 mb-2">Email</label>
            <input
              type="email"
              id="email"
              class="w-full px-4 py-3 rounded-lg border border-gray-200 focus:border-primary focus:ring-2 focus:ring-primary/20 outline-none transition-all"
              placeholder="john@example.com"
            />
          </div>
        </div>
        <div>
          <label for="message" class="block text-sm font-medium text-dark/70 mb-2">Message</label>
          <textarea
            id="message"
            rows="5"
            class="w-full px-4 py-3 rounded-lg border border-gray-200 focus:border-primary focus:ring-2 focus:ring-primary/20 outline-none transition-all resize-none"
            placeholder="Tell me about your project..."
          ></textarea>
        </div>
        <div class="flex justify-center">
          <button
            type="submit"
            class="px-8 py-3 bg-primary hover:bg-secondary text-white font-semibold rounded-full transition-colors"
          >
            Send Message
          </button>
        </div>
      </form>
    </div>
  </div>
</section>