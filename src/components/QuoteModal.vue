<template>
  <Transition name="fade">
    <div
      v-show="modelValue"
      class="fixed inset-0 z-[100] flex items-center justify-center p-4 bg-blue-900/60 backdrop-blur-sm"
      @click.self="closeModal"
    >
      <div
        class="relative bg-white w-full max-w-4xl rounded-2xl overflow-hidden shadow-2xl flex flex-col md:flex-row border border-blue-100 animate-modal"
      >
        <button
          @click="closeModal"
          type="button"
          class="absolute top-4 right-4 z-20 bg-white/90 hover:bg-red-50 rounded-full p-2 text-blue-900 hover:text-red-600 transition-all shadow-sm"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-6 w-6"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            />
          </svg>
        </button>

        <div class="w-full md:w-1/2 p-8 lg:p-12">
          <h2 class="text-3xl font-black text-blue-900 uppercase mb-2">
            Get Your <span class="text-blue-600">Quote</span>
          </h2>
          <p class="text-blue-500 text-sm mb-6">
            Fast, easy, and commitment-free cleaning quotes.
          </p>

          <form @submit.prevent="handleSubmit" class="space-y-4">
            <input
              v-model="form.name"
              type="text"
              placeholder="Full Name*"
              required
              class="w-full px-4 py-3 rounded-lg border border-blue-100 bg-blue-50/30 focus:ring-2 focus:ring-blue-500 outline-none transition-all"
            />

            <div class="flex">
              <div
                class="inline-flex items-center px-3 rounded-l-lg border border-r-0 border-blue-100 bg-blue-50/50"
              >
                🇧🇩
              </div>
              <input
                v-model="form.phone"
                type="tel"
                placeholder="Phone*"
                required
                class="w-full px-4 py-3 rounded-r-lg border border-blue-100 bg-blue-50/30 focus:ring-2 focus:ring-blue-500 outline-none transition-all"
              />
            </div>

            <input
              v-model="form.email"
              type="email"
              placeholder="Email Address*"
              required
              class="w-full px-4 py-3 rounded-lg border border-blue-100 bg-blue-50/30 focus:ring-2 focus:ring-blue-500 outline-none transition-all"
            />

            <select
              v-model="form.cleanType"
              required
              class="w-full px-4 py-3 rounded-lg border border-blue-100 bg-blue-50/30 text-gray-500 focus:ring-2 focus:ring-blue-500 outline-none"
            >
              <option value="" disabled>What Type of Clean</option>
              <option value="standard">Standard</option>
              <option value="deep">Deep Clean</option>
            </select>

            <button
              type="submit"
              class="w-full bg-blue-600 hover:bg-blue-700 text-white font-bold py-4 rounded-lg transition-all transform active:scale-95 uppercase shadow-lg"
            >
              Submit Request
            </button>
          </form>
        </div>

        <div class="hidden md:block md:w-1/2 relative">
          <img
            src="https://images.unsplash.com/photo-1584622650111-993a426fbf0a?auto=format&fit=crop&q=80&w=800"
            class="absolute inset-0 h-full w-full object-cover"
            alt="Cleaning service"
          />
          <div class="absolute inset-0 bg-blue-900/10"></div>
        </div>
      </div>
    </div>
  </Transition>
</template>

<script setup>
import { reactive, onMounted } from "vue";

const props = defineProps(["modelValue"]);
const emit = defineEmits(["update:modelValue"]);

const form = reactive({ name: "", phone: "", email: "", cleanType: "" });

// "Auto-open" logic: কম্পোনেন্ট লোড হওয়ার পর প্যারেন্টকে বলবে ওপেন হতে
onMounted(() => {
  setTimeout(() => {
    emit("update:modelValue", true);
  }, 500); // পেজ লোডের ৫০০ms পর ওপেন হবে
});

const closeModal = () => emit("update:modelValue", false);

const handleSubmit = () => {
  console.log("Data Submitted:", form);
  alert("Thank you! Your quote request has been sent.");
  closeModal();
};
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.4s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

@keyframes modalPop {
  from {
    opacity: 0;
    transform: scale(0.9) translateY(20px);
  }
  to {
    opacity: 1;
    transform: scale(1) translateY(0);
  }
}
.animate-modal {
  animation: modalPop 0.5s ease-out forwards;
}
</style>
