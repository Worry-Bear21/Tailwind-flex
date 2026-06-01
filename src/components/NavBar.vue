<template>
  <div class="font-[Arial] bg-white fixed top-0 left-0 w-full z-[999] shadow-sm">

    <div class="border-b border-gray-100 relative">
      <div class="max-w-7xl mx-auto px-4 flex justify-end items-center py-2 text-[12px]">
        <p href="#" @click="addModal" class="text-[#ED2846] hover:underline px-2 cursor-pointer">FEEDBACK</p>
        <span class="text-gray-300">|</span>

        <p href="#" @click="savemorebtn" class="text-[#666666] hover:underline px-2 cursor-pointer">
          SAVE MORE ON APP
        </p>
        <span class="text-gray-300">|</span>
        <p @click="navigate('home')" class="text-[#333333] hover:underline px-2 cursor-pointer">SELL ON LAZADA</p>
        <span class="text-gray-300">|</span>
        <p href="#" @click="custommodalbtn" class="text-[#666666] hover:underline px-2 cursor-pointer">CUSTOMER CARE</p>
        <span class="text-gray-300">|</span>
        <p href="#" @click="navigate('showCart')" class="text-[#666666] hover:underline px-2 cursor-pointer">TRACK MY
          ORDER</p>
        <span class="text-gray-300">|</span>
        <p href="#" class="text-[#666666] hover:underline px-2 cursor-pointer">LOGIN</p>
        <span class="text-gray-300">|</span>
        <p href="#" class="text-[#666666] hover:underline px-2 cursor-pointer">SIGNUP</p>
      </div>

      <CustomModal v-if="showCustomModal" class="absolute right-10 top-[100%] mt-1 -translate-x-1/2 z-[9999]" />
      <Savemore v-if="showSaveMore" class="absolute left-1/2 top-[100%] mt-1 -translate-x-1/2 z-[9999]" />
    </div>


    <div class="max-w-7xl mx-auto px-4 py-3 flex items-center gap-6">

      <div class="flex items-center w-[120px]">
        <img src="https://img.lazcdn.com/g/tps/images/ims-web/TB19SB7aMFY.1VjSZFnXXcFHXXa.png" alt="Lazada Logo"
          class="w-full h-auto">
      </div>

      <div class="flex-1 flex items-center">
        <input v-model="searchbar" type="text" placeholder="Search in Lazada"
          class="w-full bg-[#F5F5F5] px-4 py-2.5 text-[#333333] text-sm focus:outline-none border border-gray-200 rounded-l-sm">
        <button class="bg-[#EE4D2D] text-white px-5 py-2.5 rounded-r-sm hover:bg-[#D44226] transition-colors">
          <svg class="w-5 h-5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none"
            viewBox="0 0 24 24">
            <path stroke="currentColor" stroke-linecap="round" stroke-width="2"
              d="m21 21-3.5-3.5M17 10a7 7 0 1 1-14 0 7 7 0 0 1 14 0Z" />
          </svg>
        </button>
      </div>
      <!-- Cart Icon -->
      <svg class="w-6 h-6 text-[#333333] hover:text-[#EE4D2D] cursor-pointer transition-colors" aria-hidden="true"
        xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24">
        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
          d="M5 4h1.5L9 16m0 0h8m-8 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4Zm8 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4Zm-8.5-3h9.25L19 7H7.312" />
      </svg>
      <!-- Lazada Loans -->
      <div class="flex items-center gap-3">
        <p href="#"
          class="bg-gradient-to-r from-[#ED2846] to-[#FF5722] text-white text-[12px] font-bold px-4 py-1.5 rounded-sm hover:shadow-md transition-shadow">
          APPLY NOW <span class="text-[9px] font-normal">WITH ₱</span>
        </p>
        <span class="text-[#5E2593] font-semibold text-sm flex items-center gap-1">
          <svg width="16" height="16" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M16 0L24 8L16 16L8 8L16 0Z" fill="#FF6A00" />
            <path d="M16 16L24 24L16 32L8 24L16 16Z" fill="#5E2593" />
            <path d="M24 8L32 16L24 24L16 16L24 8Z" fill="#FF0080" />
          </svg>
          Lazada Loans
        </span>
      </div>
    </div>
  </div>
</template>

<script>
import Savemore from './Savemore.vue';
import CustomModal from './CustomModal.vue';

export default {
  components: { Savemore, CustomModal },
  props: {
    cart: {
      type: Array
    }
  },
  data() {
    return {
      showSaveMore: false,
      showCustomModal: false,
      searchbar: '',
    };
  },
  computed: {
    filteredProducts() {
      if (!this.searchbar.trim()) {
        return this.products
      }
      const query = this.searchbar.toLowerCase().trim();
      return this.products.filter(product =>
        product.name.toLowerCase().includes(query)
      )
    }
  },
  methods: {
    savemorebtn() {
      this.showSaveMore = true;
    },
    custommodalbtn() {
      this.showCustomModal = true;
    },
    addModal() {
      this.$emit('openAddModal')
    },
    navigate(page) {
      this.$emit('goTo', page)
    }
  }
}
</script>