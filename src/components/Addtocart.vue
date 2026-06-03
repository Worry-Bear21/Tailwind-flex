<template>
  <div class="bg-gray-100 dark:bg-gray-900 w-full min-h-screen pt-24 px-4 sm:px-8 lg:px-16">
    <div class="max-w-7xl mx-auto py-10">
      <h2 class="text-2xl font-bold text-gray-800 dark:text-white mb-8">My Cart</h2>

      <div v-if="cartitems.length > 0" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
        <div v-for="item in cartitems" :key="item.id"
          class="bg-gray-800 rounded-xl shadow-lg overflow-hidden flex flex-col">
          <div class="w-full h-52 bg-gray-700/40 p-4 flex items-center justify-center">
            <img :src="item.image" :alt="item.name" class="h-full object-contain" />
          </div>

          <div class="p-4 flex flex-col flex-grow text-center">
            <h3 class="text-white font-semibold text-lg mb-2">{{ item.name }}</h3>
            <p class="text-yellow-400 font-bold text-xl mb-4">{{ item.price }}</p>


            <div class="flex gap-3 w-full justify-center">
              <button
                class="px-4 py-2 bg-yellow-500 hover:bg-yellow-600 text-black font-medium rounded-lg transition-all hover:scale-105 duration-300 cursor-pointer shadow-sm hover:shadow-md"
                @click="removeItemClicked(item.id)">Buy</button>

              <div class="flex gap-2 mt-auto">
                <button @click="removeItemClicked(item.id)"
                  class="flex-1 bg-red-500 hover:bg-red-600 text-white py-2 rounded-lg">

                  Remove
                </button>
                <button @click="checkoutClicked"
                  class="flex-1 bg-blue-600 hover:bg-blue-700 text-white py-2 rounded-lg">
                  Checkout
                </button>
              </div>
            </div>
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
      required: true
    }
  },

  methods: {
    addOrder() {
      this.$emit('Order', this.cartitems);
      this.removeItemClicked()
      alert('✅ Successfully added to Order!');
    },
    methods: {
      removeItemClicked(id) {

      },
      checkoutClicked() {
        this.$emit('addToOrder', this.cartitems);
      },
      removeItemClicked(id) {

        this.$emit('removeFromCart', id);
      }
    }
  }
}
</script>