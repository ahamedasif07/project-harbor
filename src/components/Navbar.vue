<template>
  <nav
    class="flex items-center justify-between px-6 py-4 bg-white shadow-sm sticky top-0 z-50"
  >
    <div class="flex items-center space-x-2">
      <div
        class="w-10 h-10 bg-blue-600 rounded-full flex items-center justify-center"
      >
        <span class="text-white font-bold text-xs text-center leading-none"
          >DSC</span
        >
      </div>
      <span class="font-bold text-xl text-blue-900 hidden sm:inline-block"
        >Desert Sky</span
      >
    </div>

    <div
      class="hidden md:flex items-center space-x-8 text-blue-900 font-medium"
    >
      <a href="#" class="hover:text-blue-600 transition">HOME</a>
      <a href="#" class="hover:text-blue-600 transition">ABOUT</a>
      <a href="#" class="hover:text-blue-600 transition">SERVICES</a>
      <button
        class="bg-blue-600 text-white px-6 py-2 rounded shadow-md hover:bg-blue-700 transition"
      >
        CALL US NOW
      </button>
    </div>

    <div class="md:hidden text-blue-900 text-2xl">
      <button>☰</button>
    </div>
  </nav>
</template>
