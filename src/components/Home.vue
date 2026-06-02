<template>
  <div class="bg-gray-100 dark:bg-gray-900 w-full min-h-screen pt-24 px-4 sm:px-8 lg:px-16">
    <div class="max-w-7xl mx-auto py-10">
      <h2 class="text-2xl font-bold text-gray-800 dark:text-white mb-8 text-center">Featured Products</h2>

      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
        
        <!-- ✅ ANG LISTAHAN SA PRODUKTO -->
        <div 
          v-for="product in filteredProducts" 
          :key="product.id"
          class="bg-gray-800 rounded-xl shadow-lg overflow-hidden hover:shadow-2xl hover:-translate-y-1 transition-all duration-300 flex flex-col"
        >
          <div class="w-full h-52 bg-gray-700/40 p-4 flex items-center justify-center">
            <img :src="product.image" :alt="product.name" class="h-full object-contain hover:scale-105 transition-transform duration-300"/>
          </div>

          <div class="p-4 flex flex-col flex-grow text-center">
            <h3 class="text-white font-semibold text-lg mb-2 line-clamp-2 h-12">{{ product.name }}</h3>
            <p class="text-yellow-400 font-bold text-xl mb-4">{{ product.price }}</p>

            <div class="flex flex-col gap-2 mt-auto">
              <!-- Imong daan nga mga buton -->
              <div class="flex gap-2">
                <button @click="addToCartClicked(product)" class="flex-1 bg-yellow-500 hover:bg-yellow-600 text-black font-medium py-2 rounded-lg">
                  Add to Cart
                </button>
                <button @click="buyNowClicked(product)" class="flex-1 bg-green-600 hover:bg-green-700 text-white font-medium py-2 rounded-lg">
                  Buy Now
                </button>
              </div>

              <!-- ✅ DINHI GYUD IBUTANG ANG VIEW DETAILS BUTTON -->
              <button 
                @click="openProductModal(product)" 
                class="w-full bg-blue-500 hover:bg-blue-600 text-white font-medium py-2 rounded-lg transition-colors"
              >
                View Details
              </button>
            </div>
          </div>
        </div>

      </div>
    </div>

    <!-- ✅ DINHI SA UBOS, SA GAWAS SA LISTAHAN - ANG IMONG MODAL.VUE -->
    <Modal 
      v-if="showModal" 
      :selectedProduct="selectedProduct" 
      @addToCart="addToCartClicked" 
      @close="closeProductModal"
    />

  </div>
</template>

<script>
// ✅ SAKTO NGA PANGALAN: Modal (kay Modal.vue man ang imoha)
import Modal from './Modal.vue'

export default {
  // ✅ I-DECLARE ANG COMPONENT
  components: { Modal },

  props: {
    addingProduct: Boolean,
    searchbar: String
  },
  data() {
    return {
      products: [
        { id: 1, name: "Wireless Headphones Pro", price: "₱ 1,299.00", image: "https://tse1.mm.bing.net/th/id/OIP.7sJ9aK4QrHdUeK8zL7xQgwHaHa?w=200&h=200&c=7" },
        { id: 2, name: "Smart Watch Series 7", price: "₱ 2,499.00", image: "https://tse1.mm.bing.net/th/id/OIP.x8ZbJ4QrHdUeK8zL7xQgwHaHa?w=200&h=200&c=7" },
        { id: 3, name: "Bluetooth Speaker Mini", price: "₱ 499.00", image: "https://tse1.mm.bing.net/th/id/OIP.9sK9aK4QrHdUeK8zL7xQgwHaHa?w=200&h=200&c=7" },
        { id: 4, name: "Power Bank 20000mAh", price: "₱ 799.00", image: "https://tse1.mm.bing.net/th/id/OIP.b8ZbJ4QrHdUeK8zL7xQgwHaHa?w=200&h=200&c=7" }
      ],

      // ✅ KINI ANG GIHIMO PARA SA MODAL
      selectedProduct: null,
      showModal: false
    }
  },
  computed: {
    filteredProducts() {
      if (!this.searchbar) return this.products;
      return this.products.filter(p => p.name.toLowerCase().includes(this.searchbar.toLowerCase()));
    }
  },
  methods: {
    // ✅ ABLIHAN ANG MODAL UG IPASA ANG PRODUKTO
    openProductModal(product) {
      this.selectedProduct = product;
      this.showModal = true;
    },
    // ✅ ISIRA ANG MODAL
    closeProductModal() {
      this.showModal = false;
      this.selectedProduct = null;
    },

    // ✅ IMONG DAAN NGA FUNCTIONS
    addToCartClicked(product) {
      this.$emit('addToCart', product);
      // Inig pislit gikan sa Modal, isira dayon
      this.closeProductModal(); 
    },
    buyNowClicked(product) {
      this.$emit('addToOrder', product);
    }
  }
}
</script>