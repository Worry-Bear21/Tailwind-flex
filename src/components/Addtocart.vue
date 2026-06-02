<template>
  <div class="bg-gray-200 w-full min-h-screen p-8 sm:p-16 dark:bg-gray-900 mt-10">

    <div class="max-w-7xl mx-auto mb-10">
      <h2 class="text-2xl font-bold text-gray-800 dark:text-white mb-6">My Cart</h2>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-8">
        <div v-for="item in cartitems" :key="item.id"
          class="group h-[420px] shadow-lg rounded-2xl overflow-hidden transition-all duration-300 hover:shadow-2xl hover:-translate-y-1"
          style="background-color: #1a202c;">
          <!-- Product Image -->
          <div class="p-4 h-3/5 flex items-center justify-center bg-gray-800/50">
            <img class="w-full h-full object-contain hover:cursor-pointer hover:scale-105 duration-300"
              :src="item.image" alt="product image" />
          </div>

          <!-- Product Info & Actions -->
          <div class="px-6 pb-6 pt-4 h-2/5 flex flex-col justify-center items-center text-center">
            <p
              class="hover:text-yellow-400 cursor-pointer font-semibold text-lg mb-2 transition-colors duration-200 text-white line-clamp-2">
              {{ item.name }}
            </p>
            <p class="text-gray-300 text-base font-medium mb-3">₱ {{ item.price }}</p>

            <!-- Action Buttons -->
            <div class="flex gap-3 w-full justify-center">
              <button
                class="px-4 py-2 bg-yellow-500 hover:bg-yellow-600 text-black font-medium rounded-lg transition-all hover:scale-105 duration-300 cursor-pointer shadow-sm hover:shadow-md"
                @click="removeItem(item.id)">
                Remove
              </button>
              <button
                class="px-4 py-2 bg-blue-600 hover:bg-blue-700 text-white font-medium rounded-lg transition-all hover:scale-105 duration-300 cursor-pointer shadow-sm hover:shadow-md"
                @click="buyNow(item)">
                Buy Now
              </button>
            </div>
          </div>
        </div>
      </div>

      <!-- Empty Cart State -->
      <div v-if="cartitems.length === 0" class="text-center py-16">
        <p class="text-gray-600 dark:text-gray-300 text-lg">Your cart is empty.</p>
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