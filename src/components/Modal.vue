<template>
  <div class="flex items-center justify-center h-screen fixed top-0 inset-0 bg-black/50">
    <div class="w-80 border border-blue-200 rounded-lg shadow-md p-4 bg-white">
      <div class="relative">
        <span
          class="absolute top-2 left-2 bg-orange-400 text-white text-xs font-semibold px-2 py-1 rounded-full">-20%</span>

        <button class="absolute top-2 right-2 w-8 h-8 bg-white rounded-full shadow flex items-center justify-center">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 text-gray-600" fill="none" viewBox="0 0 24 24"
            stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round"
              d="M20.84 4.61a5.5 5.5 0 00-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 00-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 000-7.78z" />
          </svg>
        </button>
        <div class="mt-8">
          <img :src="selectedProduct.image" alt="Product Image" class="object-contain w-full h-[270px]" />
        </div>
      </div>

      <div class="mt-4">
        <h3 class="text-gray-800 font-medium text-base">{{ selectedProduct.name }}</h3>
        <p class="uppercase text-green-600 text-xs font-medium mt-1">Oraimo</p>
        <div class="flex space-x-1 text-orange-500 text-sm mt-1">
          <svg v-for="star in 5" :key="star" xmlns="http://www.w3.org/2000/svg" class="h-4 w-4"
            :fill="star <= 4 ? 'currentColor' : '#d1d5db'" viewBox="0 0 20 20">
            <path
              d="M9.049 2.927C9.349 2.2 10.651 2.2 10.951 2.927l1.558 3.779 4.004.37c.85.079 1.194 1.139.572 1.724l-2.922 2.658.87 3.917c.181.816-.68 1.448-1.419 1.034L10 13.01l-3.614 1.96c-.74.414-1.6-.218-1.419-1.034l.87-3.917-2.922-2.658c-.622-.585-.278-1.645.572-1.724l4.004-.37L9.049 2.927z" />
          </svg>
        </div>
        <div class="flex items-end justify-between mt-2">
          <div class="flex items-baseline space-x-2">{{ selectedProduct.price }}</div>
          <button class="w-10 h-10 rounded-full bg-blue-600 flex items-center justify-center shadow text-white">
            <svg @click="add" class="cursor-pointer" xmlns="http://www.w3.org/2000/svg" width="20" height="20"
              viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"
              stroke-linejoin="round">
              <path stroke="none" d="M0 0h24v24H0z" fill="none" />
              <path d="M6 19m-2 0a2 2 0 1 0 4 0a2 2 0 1 0 -4 0" />
              <path d="M17 19m-2 0a2 2 0 1 0 4 0a2 2 0 1 0 -4 0" />
              <path d="M17 17h-11v-14h-2" />
              <path d="M6 5l14 1l-1 7h-13" />
            </svg>
          </button>
        </div>
        <button @click="closeModal"
          class="w-full border flex justify-center items-center text-center px-3 rounded-md bg-red-500 cursor-pointer hover:bg-green-500 hover:scale-105 duration-300 mt-3 py-2">Confirm</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    selectedProduct: {
      type: Object,
    }
  },
  methods: {
    add() {
      this.$emit('addTocart', this.selectedProduct);
    },
    closeModal() {
      this.$emit('close');
    }
  }
}
</script>