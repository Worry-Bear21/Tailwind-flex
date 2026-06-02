<template>
  <div class="font-[Arial] bg-[#1a202c] fixed top-0 left-0 w-full z-[999] shadow-lg">
    <div class="border-b border-gray-700 relative">
      <div class="max-w-7xl mx-auto px-4 flex justify-end items-center py-2 text-[12px] gap-1">
        <p @click="addModal" class="text-[#ED2846] hover:text-[#ff4a5f] hover:underline px-2 cursor-pointer">FEEDBACK</p>
        <span class="text-gray-600">|</span>
        <p @click="savemorebtn" class="text-gray-300 hover:text-white hover:underline px-2 cursor-pointer">SAVE MORE ON APP</p>
        <span class="text-gray-600">|</span>
        
        <!-- ✅ SAKTO NGA PANGALAN: 'home' (gamay tanan) -->
        <p @click="navigate('home')" class="text-gray-200 hover:text-white hover:underline px-2 cursor-pointer">SELL ON LAZADA</p>
        <span class="text-gray-600">|</span>

        <div class="relative inline-block">
          <p @click="custommodalbtn" class="text-gray-300 hover:text-white hover:underline px-2 cursor-pointer">CUSTOMER CARE</p>
          <CustomModal v-if="showCustomModal" class="absolute left-0 top-[100%] mt-1 w-[260px] bg-[#1e293b] rounded-md shadow-lg border border-gray-700 py-2 z-[9999]" />
        </div>
        <span class="text-gray-600">|</span>

        <!-- ✅ SAKTO NGA PANGALAN: 'showOrder' -->
        <p @click="navigate('showOrder')" class="text-gray-300 hover:text-white hover:underline px-2 cursor-pointer">ORDER HISTORY</p>
        <span class="text-gray-600">|</span>
        <p class="text-gray-300 hover:text-white hover:underline px-2 cursor-pointer">LOGIN</p>
        <span class="text-gray-600">|</span>
        <p class="text-gray-300 hover:text-white hover:underline px-2 cursor-pointer">SIGNUP</p>
      </div>
    </div>

    <div class="max-w-7xl mx-auto px-4 py-4 flex items-center gap-6">
      <!-- ✅ SA LOGO: SAKTO USAB 'home' -->
      <div @click="navigate('home')" class="flex items-center w-[120px] cursor-pointer">
        <img src="https://tse1.mm.bing.net/th/id/OIP.aV2au23ZP-jyEmJz0rDjKwHaG2?pid=ImgDet&w=474&h=438&rs=1&o=7&rm=3" alt="Lazada Logo" class="w-full h-20 object-contain">
      </div>

      <div class="flex-1 flex items-center">
        <input v-model="searchbar" @input="delsearch" type="text" placeholder="Search in Lazada" class="w-full bg-gray-800 text-gray-200 px-4 py-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-[#EE4D2D]/40 border border-gray-700 rounded-l-lg">
        <button class="bg-[#EE4D2D] text-white px-5 py-2.5 rounded-r-lg hover:bg-[#D44226]">
          <svg class="w-5 h-5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24">
            <path stroke="currentColor" stroke-linecap="round" stroke-width="2" d="m21 21-3.5-3.5M17 10a7 7 0 1 1-14 0 7 7 0 0 1 14 0Z" />
          </svg>
        </button>
      </div>

      <!-- ✅ SA CART: SAKTO NGA PANGALAN: 'cart' -->
      <svg @click="navigate('cart')" class="w-6 h-6 text-gray-200 hover:text-[#EE4D2D] cursor-pointer transition-all" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24">
        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 4h1.5L9 16m0 0h8m-8 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4Zm8 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4Zm-8.5-3h9.25L19 7H7.312" />
      </svg>

      <div class="flex items-center gap-4">
        <p class="bg-gradient-to-r from-[#ED2846] to-[#FF5722] text-white text-[12px] font-bold px-4 py-2 rounded-lg">APPLY NOW <span class="text-[9px] font-normal">WITH ₱</span></p>
        <span class="text-[#d1b8f0] font-semibold text-sm flex items-center gap-1.5">
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
  props: { cart: Array },
  data() {
    return { showSaveMore: false, showCustomModal: false, searchbar: '' };
  },
  methods: {
    delsearch() { this.$emit('handleSearch', this.searchbar) },
    savemorebtn() { this.showSaveMore = true; },
    custommodalbtn() { this.showCustomModal = true; },
    addModal() { this.$emit('openAddModal') },
    // ✅ DINHI IPASA ANG PANGALAN SA PANID
    navigate(page) { 
      console.log('Gipadala:', page); // 🔍 PARA SA PAGSUSI
      this.$emit('goTo', page) 
    }
  }
}
</script>