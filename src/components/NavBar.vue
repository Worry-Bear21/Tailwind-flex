20260602 06:56:45 || 20260602 07:04:22 || <template>
  <div class="font-[Arial] bg-[#1a202c] fixed top-0 left-0 w-full z-[999] shadow-lg">

    <div class="border-b border-gray-700 relative">
      <div class="max-w-7xl mx-auto px-4 flex justify-end items-center py-2 text-[12px] gap-1">
        <p @click="addModal"
          class="text-[#ED2846] hover:text-[#ff4a5f] hover:underline px-2 cursor-pointer transition-colors duration-200">
          FEEDBACK
        </p>
        <span class="text-gray-600">|</span>

        <p @click="savemorebtn"
          class="text-gray-300 hover:text-white hover:underline px-2 cursor-pointer transition-colors duration-200">
          SAVE MORE ON APP
        </p>
        <span class="text-gray-600">|</span>

        <p @click="navigate('home')"
          class="text-gray-200 hover:text-white hover:underline px-2 cursor-pointer transition-colors duration-200">
          SELL ON LAZADA
        </p>
        <span class="text-gray-600">|</span>

        <p @click="custommodalbtn"
          class="text-gray-300 hover:text-white hover:underline px-2 cursor-pointer transition-colors duration-200">
          CUSTOMER CARE
        </p>
        <span class="text-gray-600">|</span>

        <p @click="navigate('showCart')"
          class="text-gray-300 hover:text-white hover:underline px-2 cursor-pointer transition-colors duration-200">
          TRACK MY ORDER
        </p>
        <span class="text-gray-600">|</span>

        <p class="text-gray-300 hover:text-white hover:underline px-2 cursor-pointer transition-colors duration-200">
          LOGIN
        </p>
        <span class="text-gray-600">|</span>

        <p class="text-gray-300 hover:text-white hover:underline px-2 cursor-pointer transition-colors duration-200">
          SIGNUP
        </p>
      </div>

      <CustomModal v-if="showCustomModal"
        class="absolute right-6 top-[100%] mt-2 z-[9999] shadow-lg rounded-lg overflow-hidden" />
      <Savemore v-if="showSaveMore"
        class="absolute left-1/2 top-[100%] mt-2 -translate-x-1/2 z-[9999] shadow-lg rounded-lg overflow-hidden" />
    </div>


    <div class="max-w-7xl mx-auto px-4 py-4 flex items-center gap-6">
      <!-- Logo -->
      <div class="flex items-center w-[120px]">
        <img src="" alt="Lazada Logo" class="w-full h-auto object-contain">
      </div>

      <!-- Search Bar -->
      <div class="flex-1 flex items-center">
        
        <input v-model="localSearch" type="text" placeholder="Search in Lazada" @input="delsearch"
          class="w-full bg-gray-800 text-gray-200 px-4 py-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-[#EE4D2D]/40 border border-gray-700 rounded-l-lg transition-all placeholder:text-gray-400">
        <button
          class="bg-[#EE4D2D] text-white px-5 py-2.5 rounded-r-lg hover:bg-[#D44226] hover:shadow-md transition-all duration-200">
          <svg class="w-5 h-5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none"
            viewBox="0 0 24 24">
            <path stroke="currentColor" stroke-linecap="round" stroke-width="2"
              d="m21 21-3.5-3.5M17 10a7 7 0 1 1-14 0 7 7 0 0 1 14 0Z" />
          </svg>
        </button>
      </div>

      <!-- Cart Icon -->
      <svg @click="navigate('showCart')"
        class="w-6 h-6 text-gray-200 hover:text-[#EE4D2D] cursor-pointer transition-all duration-200 hover:scale-110"
        aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24">
        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
          d="M5 4h1.5L9 16m0 0h8m-8 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4Zm8 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4Zm-8.5-3h9.25L19 7H7.312" />
      </svg>

      <!-- Lazada Loans -->
      <div class="flex items-center gap-4">
        <p
          class="bg-gradient-to-r from-[#ED2846] to-[#FF5722] text-white text-[12px] font-bold px-4 py-2 rounded-lg hover:shadow-lg hover:-translate-y-[1px] transition-all duration-200 cursor-pointer">
          APPLY NOW <span class="text-[9px] font-normal">WITH ₱</span>
        </p>
        <span
          class="text-[#d1b8f0] font-semibold text-sm flex items-center gap-1.5 hover:text-white hover:opacity-90 cursor-pointer transition-all">
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
      localSearch: '', 
    };
  },
 
  methods: {
    
    delsearch() {
      this.$emit('update-search', this.localSearch)
    },
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