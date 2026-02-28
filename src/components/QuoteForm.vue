<script setup>
import { reactive } from "vue";

const formData = reactive({
  firstName: "",
  lastName: "",
  phone: "",
  email: "",
  cleanType: "",
  agreed: false,
});

const handleSubmit = () => {
  console.log("Data Submitted:", formData);
  alert("Quote Request Received!");
};
</script>

<template>
  <form @submit.prevent="handleSubmit" class="space-y-4">
    <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
      <input
        v-model="formData.firstName"
        type="text"
        placeholder="First Name*"
        class="w-full bg-white border border-transparent text-gray-800 rounded-xl px-4 py-4 text-[15px] shadow-sm focus:ring-2 focus:ring-blue-400 focus:outline-none transition-all placeholder:text-gray-400"
        required
      />
      <input
        v-model="formData.lastName"
        type="text"
        placeholder="Last Name*"
        class="w-full bg-white border border-transparent text-gray-800 rounded-xl px-4 py-4 text-[15px] shadow-sm focus:ring-2 focus:ring-blue-400 focus:outline-none transition-all placeholder:text-gray-400"
        required
      />
    </div>

    <div class="relative group">
      <div
        class="absolute inset-y-0 left-0 flex items-center pl-4 pr-2 border-r border-blue-100 my-3 cursor-pointer"
      >
        <span class="text-xl mr-1">🇧🇩</span>
        <svg
          class="w-3 h-3 text-gray-500"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M19 9l-7 7-7-7"
          />
        </svg>
      </div>
      <input
        v-model="formData.phone"
        type="tel"
        placeholder="Phone No.*"
        class="w-full pl-20 bg-white border border-transparent text-gray-800 rounded-xl px-4 py-4 text-[15px] shadow-sm focus:ring-2 focus:ring-blue-400 focus:outline-none transition-all placeholder:text-gray-400"
        required
      />
    </div>

    <input
      v-model="formData.email"
      type="email"
      placeholder="Email*"
      class="w-full bg-white border border-transparent text-gray-800 rounded-xl px-4 py-4 text-[15px] shadow-sm focus:ring-2 focus:ring-blue-400 focus:outline-none transition-all placeholder:text-gray-400"
      required
    />

    <div class="relative">
      <select
        v-model="formData.cleanType"
        class="w-full bg-white border border-transparent text-blue-900 rounded-xl px-4 py-4 text-[15px] shadow-sm focus:ring-2 focus:ring-blue-400 focus:outline-none transition-all appearance-none cursor-pointer"
        required
      >
        <option value="" disabled selected class="text-gray-400">
          What Type of Clean*
        </option>
        <option
          value="standard"
          class="py-2 hover:bg-blue-600 hover:text-white"
        >
          Standard Clean
        </option>
        <option value="deep" class="py-2 hover:bg-blue-600 hover:text-white">
          Deep Clean
        </option>
        <option value="moving" class="py-2 hover:bg-blue-600 hover:text-white">
          Move In / Move Out
        </option>
      </select>

      <div
        class="absolute inset-y-0 right-0 flex items-center pr-4 pointer-events-none"
      >
        <svg
          class="w-5 h-5 text-blue-900"
          fill="currentColor"
          viewBox="0 0 20 20"
        >
          <path
            d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
          />
        </svg>
      </div>
    </div>

    <div class="flex items-start gap-3 py-2 px-1">
      <input
        v-model="formData.agreed"
        type="checkbox"
        id="terms"
        class="mt-1 min-w-[16px] h-4 rounded border-blue-200 text-blue-600 focus:ring-blue-500 cursor-pointer"
        required
      />
      <label
        for="terms"
        class="text-[12px] sm:text-[13px] text-blue-900 font-medium cursor-pointer leading-snug"
      >
        By checking this box you agree to our
        <a
          href="#"
          class="text-blue-600 underline hover:text-blue-800 transition"
          >Terms and Conditions.</a
        >
      </label>
    </div>

    <button
      type="submit"
      class="w-full bg-blue-600 text-white font-bold py-4 rounded-xl shadow-lg hover:bg-blue-700 active:scale-[0.98] transition-all duration-200 text-base sm:text-lg tracking-wide mt-2"
    >
      Get My Quote
    </button>
  </form>
</template>
