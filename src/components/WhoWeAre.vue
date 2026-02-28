<template>
  <section
    class="relative bg-blue-50 pt-20 pb-32 lg:pt-28 lg:pb-44 overflow-hidden"
  >
    <div class="container mx-auto px-6 lg:px-12 relative z-10">
      <div
        class="flex flex-col lg:flex-row items-start justify-between gap-12 lg:gap-24"
      >
        <div class="w-full lg:w-1/4 flex flex-col items-center lg:items-start">
          <h2
            class="text-4xl md:text-5xl font-serif text-blue-900 mb-10 italic whitespace-nowrap"
          >
            Who We Are
          </h2>

          <div
            class="relative w-56 h-56 md:w-64 md:h-64 flex items-center justify-center rounded-full border-2 border-blue-200 shadow-inner bg-white/50 p-4"
          >
            <div
              class="w-full h-full rounded-full border-[6px] border-blue-900 flex items-center justify-center p-6 bg-white shadow-2xl transform hover:rotate-3 transition-transform duration-700"
            >
              <div class="text-center">
                <span
                  class="block text-blue-900 font-black text-xl md:text-2xl uppercase tracking-tighter leading-none"
                  >Desert Elite</span
                >
                <div class="my-3 border-t-2 border-blue-100 w-full"></div>
                <span
                  class="block text-blue-500 font-bold text-xs md:text-sm tracking-[0.2em]"
                  >CLEANERS</span
                >
              </div>
            </div>
          </div>
        </div>

        <div class="w-full lg:w-3/4 text-left">
          <div class="max-w-5xl">
            <p
              class="text-blue-900 text-lg md:text-2xl leading-relaxed font-medium mb-8"
            >
              <span
                class="text-2xl md:text-3xl font-bold text-blue-700 block mb-4 italic"
                >Desert Elite Cleaners</span
              >
              started with one mission and that is to make life easier for busy
              people who value a clean, comfortable space without the hassle.
              Based in Scottsdale, we provide
              <span class="text-blue-700 font-bold border-b-4 border-blue-200"
                >high-quality cleaning services</span
              >
              designed to give our clients more time to focus on what matters
              most. From detailed deep cleans to ongoing maintenance, we take
              pride in creating spotless, welcoming homes and businesses.
            </p>

            <p
              class="text-blue-800/80 text-lg md:text-xl leading-relaxed font-normal italic border-l-4 border-blue-200 pl-6"
            >
              What sets us apart is our commitment to customer satisfaction
              because we believe that every clean is done with care,
              consistency, and attention to detail. At Desert Elite Cleaners, we
              believe a fresh, well-kept space isn’t just about appearances—it’s
              about comfort, peace of mind, and making everyday life a little
              easier.
            </p>
          </div>
        </div>
      </div>
    </div>

    <div
      class="absolute bottom-0 left-0 w-full overflow-hidden leading-[0] z-0"
    >
      <svg
        class="relative block w-full h-[120px] md:h-[200px] lg:h-[320px]"
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 1200 120"
        preserveAspectRatio="none"
      >
        <path
          d="M0,80 C300,120 600,120 1200,20 V120 H0 Z"
          fill="#155DFC"
        ></path>
      </svg>
    </div>
  </section>
</template>

<script setup></script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,700;1,700&family=Inter:wght@400;500;700&display=swap");

section {
  font-family: "Inter", sans-serif;
}

h2 {
  font-family: "Playfair Display", serif;
}

/* Adds a subtle fade to the text to make it look more premium */
p {
  text-wrap: balance;
}
</style>
