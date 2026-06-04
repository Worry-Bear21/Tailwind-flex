<template>
  <div class="mt-12 border-t border-gray-700 pt-8">
    <h2 class="text-2xl font-bold text-white mb-4">🛒 Your Cart ({{ cart.length }})</h2>
    <div v-if="cart.length === 0" class="text-gray-400 text-center py-6">Your cart is empty</div>
    <div v-else class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
      <div v-for="(item, idx) in cart" :key="idx" class="bg-gray-800 p-3 rounded-lg shadow flex items-center gap-3">
        <img :src="item.image" class="w-14 h-14 object-contain" />
        <div class="text-left flex-1">
          <p class="text-white text-sm font-medium">{{ item.name }}</p>
          <p class="text-yellow-400 font-bold text-xs mt-1">{{ item.price }}</p>
        </div>
        <button @click="removeFromCart(idx)" class="text-red-500 hover:text-red-400 text-xl font-bold">×</button>
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
  },

  methods: {
    addOrder() {
      this.$emit('Order', this.cartitems);
      this.removeItemClicked()
      alert('✅ Successfully added to Order!');
    },
    methods: {
      removeItemClicked(item) {

      },
      checkoutClicked(item) {
        this.$emit('addToOrder', item);
      },
      removeItemClicked(id) {

        this.$emit('removeFromCart', item);
      }
    }
  }
}
</script>