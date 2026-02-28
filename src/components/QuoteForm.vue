<script setup>
import { reactive, ref, computed, onMounted, onUnmounted } from "vue";

// Expand this list as needed
const countries = [
  { name: "Bangladesh", code: "+880", iso: "BD", flag: "🇧🇩" },
  { name: "United States", code: "+1", iso: "US", flag: "🇺🇸" },
  { name: "United Kingdom", code: "+44", iso: "GB", flag: "🇬🇧" },
  { name: "Canada", code: "+1", iso: "CA", flag: "🇨🇦" },
  { name: "Australia", code: "+61", iso: "AU", flag: "🇦🇺" },
  { name: "India", code: "+91", iso: "IN", flag: "🇮🇳" },
  { name: "United Arab Emirates", code: "+971", iso: "AE", flag: "🇦🇪" },
  { name: "Saudi Arabia", code: "+966", iso: "SA", flag: "🇸🇦" },
];

const formData = reactive({
  firstName: "",
  lastName: "",
  phone: "",
  countryCode: "+880",
  selectedFlag: "🇧🇩",
  email: "",
  cleanType: "",
  agreed: false,
});

const isDropdownOpen = ref(false);
const searchQuery = ref("");
const dropdownRef = ref(null);

// Filter countries based on search
const filteredCountries = computed(() => {
  return countries.filter(
    (c) =>
      c.name.toLowerCase().includes(searchQuery.value.toLowerCase()) ||
      c.iso.toLowerCase().includes(searchQuery.value.toLowerCase()),
  );
});

const selectCountry = (country) => {
  formData.countryCode = country.code;
  formData.selectedFlag = country.flag;
  isDropdownOpen.value = false;
  searchQuery.value = "";
};

// Close dropdown when clicking outside
const handleClickOutside = (event) => {
  if (dropdownRef.value && !dropdownRef.value.contains(event.target)) {
    isDropdownOpen.value = false;
  }
};

onMounted(() => window.addEventListener("click", handleClickOutside));
onUnmounted(() => window.removeEventListener("click", handleClickOutside));

const handleSubmit = () => {
  console.log("Submitted:", {
    ...formData,
    fullPhone: formData.countryCode + formData.phone,
  });
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

    <div class="relative flex items-center" ref="dropdownRef">
      <button
        @click.prevent="isDropdownOpen = !isDropdownOpen"
        type="button"
        class="absolute left-0 z-20 flex items-center gap-1 pl-4 pr-2 py-4 border-r border-gray-100 h-full text-gray-700 hover:bg-gray-50 rounded-l-xl transition-all"
      >
        <span class="text-xl">{{ formData.selectedFlag }}</span>
        <svg
          class="w-3 h-3 text-gray-400"
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
      </button>

      <div
        v-if="isDropdownOpen"
        class="absolute top-full left-0 mt-2 w-72 max-h-80 overflow-hidden bg-white border border-gray-100 rounded-xl shadow-2xl z-50 flex flex-col"
      >
        <div class="p-2 bg-gray-50 border-b border-gray-100">
          <input
            v-model="searchQuery"
            type="text"
            placeholder="Search country..."
            class="w-full px-3 py-2 text-sm border border-gray-200 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-400"
          />
        </div>
        <div class="overflow-y-auto max-h-60">
          <div
            v-for="country in filteredCountries"
            :key="country.iso"
            @click="selectCountry(country)"
            class="flex items-center gap-3 px-4 py-3 hover:bg-blue-600 hover:text-white cursor-pointer transition-colors group"
          >
            <span class="text-lg">{{ country.flag }}</span>
            <span class="flex-1 text-sm font-medium">{{ country.name }}</span>
            <span class="text-xs opacity-60 group-hover:opacity-100">{{
              country.code
            }}</span>
          </div>
        </div>
      </div>

      <div class="relative w-full">
        <span
          class="absolute left-20 top-1/2 -translate-y-1/2 text-gray-400 font-medium text-[15px] pointer-events-none"
        >
          {{ formData.countryCode }}
        </span>
        <input
          v-model="formData.phone"
          type="tel"
          placeholder="Phone No.*"
          class="w-full bg-white border border-transparent text-gray-800 rounded-xl py-4 text-[15px] shadow-sm focus:ring-2 focus:ring-blue-400 focus:outline-none transition-all placeholder:text-gray-400"
          :style="{ paddingLeft: formData.countryCode.length * 9 + 85 + 'px' }"
          required
        />
      </div>
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
        <option value="" disabled selected>What Type of Clean*</option>
        <option value="standard">Standard Clean</option>
        <option value="deep">Deep Clean</option>
        <option value="moving">Move In / Move Out</option>
      </select>
      <div
        class="absolute inset-y-0 right-0 flex items-center pr-4 pointer-events-none text-blue-900"
      >
        <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20">
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
