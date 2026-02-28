<script setup>
import { ref } from "vue";
import Navbar from "./components/Navbar.vue";
import HeroSection from "./components/HeroSection.vue";
import QuoteModal from "./components/QuoteModal.vue";
import WhoWeAre from "./components/WhoWeAre.vue";

// পপআপ কন্ট্রোল করার জন্য স্টেট
const showModal = ref(false);
</script>

<template>
  <div class="min-h-screen">
    <Navbar />

    <HeroSection />
    <!-- <div class="container mx-auto px-4 py-10">
      <button
        @click="showModal = true"
        class="bg-blue-600 text-white px-6 py-2 rounded-md"
      >
        Open Modal Manually
      </button>
    </div> -->
    <QuoteModal v-model="showModal" />
    <WhoWeAre />
  </div>
</template>
