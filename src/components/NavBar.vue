<template>

  <body class="font-[Arial] ">
    <!-- Top Links Bar -->
    <div class="border-b border-gray-200 ">
      <div class="max-w-7xl mx-auto px-4 flex justify-end items-center py-2 text-[13px]">
        <a href="#" @click="addModal" class="text-lazada-pink hover:underline px-2">FEEDBACK</a>
        <span class="text-gray-300">|</span>
        <a href="#" class="text-lazada-darkText hover:underline px-2">SAVE MORE ON APP</a>
        <span class="text-gray-300">|</span>
        <a href="#" @click="navigate('home')" class="text-lazada-darkText hover:underline px-2">SELL ON LAZADA</a>
        <span class="text-gray-300">|</span>
        <a href="#" class="text-lazada-grayText hover:underline px-2">CUSTOMER CARE</a>
        <span class="text-gray-300">|</span>
        <a href="#" @click="navigate('showCart')" class="text-lazada-grayText hover:underline px-2">TRACK MY ORDER</a>
        <span class="text-gray-300">|</span>
        <a href="#" class="text-lazada-grayText hover:underline px-2">LOGIN</a>
        <span class="text-gray-300">|</span>
        <a href="#" class="text-lazada-grayText hover:underline px-2">SIGNUP</a>
      </div>
    </div>


    <div class="max-w-7xl mx-auto px-4 py-4 flex items-center gap-6">

      <div class="flex items-center w-50">
        <img src="https://img.lazcdn.com/g/tps/images/ims-web/TB19SB7aMFY.1VjSZFnXXcFHXXa.png" alt="">
      </div>

      <!-- Search Bar -->
      <div class="flex-1 flex bg-gray-200">
        <input type="text" placeholder="Search in Lazada"
          class="w-full bg-lazada-grayBg px-4 py-2 text-lazada-darkText focus:outline-none rounded-l-sm">
        <button class="bg-lazada-orange text-white px-4 rounded-r-sm hover:opacity-90">
          <svg class="w-8 h-8 text-gray-800" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="24"
            height="24" fill="none" viewBox="0 0 24 24">
            <path stroke="currentColor" stroke-linecap="round" stroke-width="2"
              d="m21 21-3.5-3.5M17 10a7 7 0 1 1-14 0 7 7 0 0 1 14 0Z" />
          </svg>

        </button>
      </div>

      <!-- Cart Icon -->
      <svg class="w-6 h-6 text-gray-800" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="24" height="24"
        fill="none" viewBox="0 0 24 24">
        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
          d="M5 4h1.5L9 16m0 0h8m-8 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4Zm8 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4Zm-8.5-3h9.25L19 7H7.312" />
      </svg>


      <!-- Lazada Loans -->
      <div class="flex items-center gap-2">
        <a href="#"
          class="bg-gradient-to-r from-pink-500 to-pink-600 text-white text-[12px] font-bold px-3 py-1 rounded-full hover:shadow-md">
          APPLY NOW <span class="text-[9px]">WITH ₱</span>
        </a>
        <span class="text-lazada-purple font-semibold text-sm flex items-center">
          <svg width="16" height="16" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg" class="mr-1">
            <path d="M16 0L24 8L16 16L8 8L16 0Z" fill="#FF6A00" />
            <path d="M16 16L24 24L16 32L8 24L16 16Z" fill="#5E2593" />
            <path d="M24 8L32 16L24 24L16 16L24 8Z" fill="#FF0080" />
          </svg>
          Lazada Loans
        </span>
      </div>
    </div>
  </body>
</template>

<script>
export default {
  props: {
    cart: {
      type: Array
    }
  },
  methods: {
    addModal() {
      this.$emit('openAddModal');
    },
    navigate(page) {
      this.$emit('goTo', page);
    }
  }
}
</script>