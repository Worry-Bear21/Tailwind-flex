<template>
  <div>
    <Navbar 
      @openAddModal="addingProduct = true" 
      @goTo="changePage" 
      @handleSearch="handleSearch" 
      :cart="cart" 
    />

   <Home 
      v-if="currentPage === 'home'" 
      :addingProduct="showaddModal" 
      :searchbar="searchbar" 
      :products="products"
      @buyNow="proceedToOrder" 
      @openProductModal="showMyModal" 
      @addToCart="addToCart" 
    />

    <Addtocart 
      v-if="currentPage === 'cart'" 
      :cartitems="cart" 
      @addToOrder="addToOrder"
      @removeFromCart="removeFromCart" 
    />

    <Order 
      v-if="currentPage === 'showOrder'" 
      :orderlist="order" 
    />

    <CustomModal 
      v-if="addingProduct" 
      @closeAddModal="addingProduct = false" 
      @submitProduct="submitProduct" 
    />

    <AddModal v-if="addingProduct" @close="closeAddModal" @submitProduct="submitProduct" />
    
    <Footer />
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Home from './components/Home.vue'
import Addtocart from './components/Addtocart.vue'
import Order from './components/Order.vue'
import CustomModal from './components/CustomModal.vue'
import AddModal from './components/AddModal.vue'
import Footer from './components/Footer.vue'

export default {
  components: { 
    Navbar, 
    Home, 
    Addtocart, 
    Order, 
    CustomModal, 
    AddModal, 
    Footer 
  },
  data() {
    return {
      addingProduct: false, 
      currentPage: 'home',
      display: "",
      num: "",
      cart: [],
      order: [],
      searchbar: ''
    }
  },
  methods: {
    changePage(page) {
      this.currentPage = page
    },

    closeAddModal() {
      this.addingProduct = false
    },

    handleSearch(search) {
      this.searchbar = search
    },
    addToOrder(products) {
      this.order.push(products);
      this.cart = [];
      this.currentPage = 'showOrder';
      alert('🎉 Order Successful!');
    },

    submitProduct(product) {
      this.addToCart(product);
      this.addingProduct = false;
    },
  }
}
</script>