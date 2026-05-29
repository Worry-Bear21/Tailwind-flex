<template>
  <div class="bg-gray-200 w-full min-h-screen p-8 sm:p-16 dark:bg-gray-900 mt-5">

    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-8">
      <div v-for="item in cartitems"
        class="group h-[420px] shadow-lg rounded-2xl overflow-hidden transition-all duration-300 hover:shadow-2xl"
        style="background-color: #1a202c;">
        <div class="p-4 h-3/5 flex items-center justify-center">
          <img class="w-full h-full object-contain hover:cursor-pointer hover:scale-105 duration-300" :src="item.image"
            alt="product image" />
        </div>

        <div class="px-6 pb-6 h-2/5 flex flex-col justify-center items-center text-center">
          <p class="hover:text-yellow-400 cursor-pointer font-semibold text-lg mb-2 transition-colors duration-200">
            {{ item.name }}
          </p>
          <p class="text-gray-300 text-base font-medium">₱ {{ item.price }}</p>

          
          <div class="mt-4 flex gap-3">
            <button class="px-3 py-1 bg-yellow-500 hover:bg-yellow-600 text-black rounded-lg transition-colors hover:scale-105 duration-300 cursor-pointer">
              Remove
            </button>
            <button class="px-3 py-1 bg-blue-600 hover:bg-blue-700 text-white rounded-lg transition-colors hover:scale-105 duration-300 cursor-pointer">
              Buy Now
            </button>
          </div>
        </div>
      </div>



    </div>
  </div>
</template>

<script>
export default {
  props: {
    cartitems: {
      type: Array,

    }
  }
}
</script>