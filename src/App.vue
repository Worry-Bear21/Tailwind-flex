<template>
  <div>
<<<<<<< HEAD
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
=======
    <Navbar @openAddModal="showaddModal = true" @navigate="navigate" @handleSearch="searchbar = $event" :cart="cart" />

    
    <Home v-if="currentPage === 'home'" :addingProduct="showaddModal" :searchbar="searchbar" :products="products"
      @buyNow="proceedToOrder" 
      @openProductModal="showMyModal" 
      @addToCart="addToCart"
      />

      <Order v-if="currentPage === 'showOrder'" :orderlist="order" />

      <Addtocart v-if="currentPage === 'cart'" :cartitems="cart" @addToOrder="addToOrder"
        @removeFromCart="removeFromCart" />

      <CustomModal v-if="showaddModal" @closeAddModal="showaddModal = false" @submitProduct="submitProduct" />

      <!-- ✅ IMONG MODAL.VUE: DAWATON ANG IYANG DUHA KA EMITS -->
      <Modal v-if="isModalOpen" :selectedProduct="activeProduct" @addToCart="addToCart" @close="hideMyModal" />
>>>>>>> aaeb6eef63149cd557542381a69b81b005791d9d
  </div>
</template>

<script>

import Modal from './components/Modal.vue'
import CustomModal from './components/CustomModal.vue'
import Navbar from './components/Navbar.vue'
import Home from './components/Home.vue'
import Addtocart from './components/Addtocart.vue'
import Order from './components/Order.vue'
<<<<<<< HEAD
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
=======

export default {
  components: { Navbar, Home, Addtocart, Order, CustomModal, Modal },
  data() {
    return {
      showaddModal: false,
      isModalOpen: false,     
      currentPage: 'home',
      cart: [],
      order: [],
      searchbar: '',
      activeProduct: null,   
      products: [
        { id: 1, name: "Dual Berettas | Angel Eyes", price: 100.00, image: "link1.jpg" },
        { id: 2, name: "Dual Berettas | Cobalt Quartz", price: 1480.00, image: "link2.jpg" },
        { id: 3, name: "Dual Berettas | Sweet Little Angels", price: 121.00, image: "link3.jpg" },
        { id: 4, name: "Dual Berettas | Flora Carnivora", price: 59.99, image: "link4.jpg" }
      ]
    }
  },
  methods: {
    navigate(page) {
      this.currentPage = page;
>>>>>>> aaeb6eef63149cd557542381a69b81b005791d9d
    },

    handleSearch(search) {
      this.searchbar = search
    },
<<<<<<< HEAD
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
=======

  addToCart(product) {
  this.cart.push({...product});
  alert('✅ Product added to cart!');
},

addToOrder(product) {
  this.order.push(product);
  this.cart = [];
  this.currentPage = 'showOrder';
  alert('🎉 Order Successful!');
},

    submitProduct(product) {
      this.addToCart(product);
      this.showaddModal = false;
    },

    
    showMyModal(product) {
      this.activeProduct = product;
      this.isModalOpen = true;
    },

    
    proceedToOrder(product) {
      this.addToOrder(product);
    },

   
    hideMyModal() {
      this.isModalOpen = false;
      this.activeProduct = null;
    },

    handleSearch(search) {
      this.searchbar = search;
    }
>>>>>>> aaeb6eef63149cd557542381a69b81b005791d9d
  }
}
</script>