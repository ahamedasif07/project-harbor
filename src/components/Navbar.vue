<template>
  <nav class="bg-white sticky top-0 z-[60] shadow-sm">
    <div class="container mx-auto px-6 lg:px-20">
      <div class="flex items-center justify-between py-1">
        <div class="flex items-center space-x-3">
          <div
            class="w-[140px] h-[100px] flex items-center justify-center overflow-hidden"
          >
            <img
              src="/public/assets/images/logo.png"
              alt="Desert Elite Logo"
              class="w-full h-full object-contain"
            />
          </div>
          <!-- <span
            class="font-bold text-xl text-blue-900 tracking-tight hidden xs:block"
          >
            Desert Sky
          </span> -->
        </div>

        <div
          class="hidden md:flex items-center space-x-8 text-blue-900 font-bold text-sm tracking-widest"
        >
          <a href="#" class="hover:text-blue-600 transition-colors">HOME</a>
          <a href="#" class="hover:text-blue-600 transition-colors">ABOUT</a>
          <a href="#" class="hover:text-blue-600 transition-colors">SERVICES</a>
          <button
            class="bg-blue-600 text-white px-6 py-2.5 rounded shadow-lg hover:bg-blue-700 transition-all active:scale-95"
          >
            CALL US NOW
          </button>
        </div>

        <div class="md:hidden flex items-center">
          <button
            @click="isOpen = !isOpen"
            class="text-blue-900 focus:outline-none p-2"
          >
            <svg
              class="h-8 w-8"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                v-if="!isOpen"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M4 6h16M4 12h16m-7 6h7"
              />
              <path
                v-else
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M6 18L18 6M6 6l12 12"
              />
            </svg>
          </button>
        </div>
      </div>

      <transition
        enter-active-class="transition duration-200 ease-out"
        enter-from-class="transform -translate-y-4 opacity-0"
        enter-to-class="transform translate-y-0 opacity-100"
        leave-active-class="transition duration-150 ease-in"
        leave-from-class="transform translate-y-0 opacity-100"
        leave-to-class="transform -translate-y-4 opacity-0"
      >
        <div
          v-if="isOpen"
          class="md:hidden bg-white border-t border-gray-100 pb-6 shadow-xl rounded-b-2xl absolute left-0 w-full px-6"
        >
          <div class="flex flex-col space-y-4 pt-4 text-blue-900 font-bold">
            <a
              href="#"
              @click="isOpen = false"
              class="py-2 hover:text-blue-600 border-b border-gray-50"
              >HOME</a
            >
            <a
              href="#"
              @click="isOpen = false"
              class="py-2 hover:text-blue-600 border-b border-gray-50"
              >ABOUT</a
            >
            <a
              href="#"
              @click="isOpen = false"
              class="py-2 hover:text-blue-600 border-b border-gray-50"
              >SERVICES</a
            >
            <button
              class="bg-blue-600 text-white px-6 py-3 rounded shadow-md w-full text-center"
            >
              CALL US NOW
            </button>
          </div>
        </div>
      </transition>
    </div>
  </nav>
</template>

<script setup>
import { ref } from "vue";

const isOpen = ref(false);
</script>

<style scoped>
/* Smooth transition for the mobile menu */
.xs\:block {
  display: block;
}
@media (max-width: 400px) {
  .xs\:block {
    display: none;
  }
}
</style>
