<script setup lang="ts">
import QuoteForm from "./QuoteForm.vue";
</script>

<template>
  <section
    class="relative w-full min-h-[700px] lg:min-h-[600px] lg:h-[85vh] flex items-center overflow-hidden py-12 lg:py-0"
  >
    <div class="absolute inset-0 z-0">
      <img
        src="https://images.unsplash.com/photo-1595526114035-0d45ed16cfbf?q=80&w=2070"
        class="w-full h-full object-cover blur-sm scale-110"
        alt="Dining Room"
      />
      <div class="absolute inset-0 bg-black/60"></div>
    </div>

    <div class="container mx-auto px-6 lg:px-20 relative z-10">
      <div
        class="grid grid-cols-1 lg:grid-cols-12 gap-12 lg:gap-8 items-center"
      >
        <div class="lg:col-span-7 space-y-6 text-center lg:text-left">
          <h1
            class="text-3xl md:text-5xl lg:text-6xl font-serif font-bold text-white drop-shadow-md leading-[1.2] lg:leading-[1.1]"
          >
            Scottsdale’s Premier <br class="hidden lg:block" />
            Cleaning Service—Your <br class="hidden lg:block" />
            Home, Our Expertise
          </h1>

          <p
            class="text-white text-lg md:text-xl lg:text-2xl font-medium drop-shadow-sm"
          >
            Reliable. Professional. Spotless Results Every Time.
          </p>

          <button
            class="inline-block mx-auto lg:mx-0 bg-blue-600 text-white px-8 py-3 rounded shadow-lg font-bold text-sm uppercase tracking-widest hover:bg-blue-700 transition-all active:scale-95"
          >
            Call Us Now
          </button>
        </div>

        <div
          class="lg:col-span-5 flex justify-center lg:justify-end mt-8 lg:mt-0"
        >
          <div
            class="bg-white p-6 sm:p-10 rounded-[2.5rem] shadow-2xl border border-blue-50 w-full max-w-[480px]"
          >
            <h2
              class="text-xl sm:text-2xl font-bold text-blue-900 mb-6 sm:mb-8 text-center leading-tight"
            >
              Get your Quote and Book in 60 seconds!
            </h2>

            <QuoteForm />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
