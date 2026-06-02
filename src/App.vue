<template>
  <div>
    <Navbar 
      @openAddModal="showaddModal = true" 
      @goTo="changePage" 
      @handleSearch="handleSearch" 
      :cart="cart" 
    />

    <Home 
      v-if="currentPage === 'home'" 
      :addingProduct="showaddModal" 
      :searchbar="searchbar"
      @addToCart="addToCart" 
      @addToOrder="addToOrder" 
      @closeAddModal="closeAddModal"
    />

    <!-- ✅ GIHIMO NAKO NGA showCart PARA PAREHAS SA IMONG NAVBAR -->
    <Addtocart 
      v-if="currentPage === 'showCart'" 
      :cartitems="cart" 
      @addToOrder="addToOrder" 
      @removeFromCart="removeFromCart"
    />

    <Order 
      v-if="currentPage === 'showOrder'" 
      :orderlist="order"
    />

    <CustomModal 
      v-if="showaddModal" 
      @closeAddModal="closeAddModal" 
      @submitProduct="submitProduct" 
    />
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Home from './components/Home.vue'
import Addtocart from './components/Addtocart.vue'
import Order from './components/Order.vue'
import CustomModal from './components/CustomModal.vue'

export default {
  components: { Navbar, Home, Addtocart, Order, CustomModal },
  data(){
    return{
      showaddModal: false,
      currentPage: 'home', // default nga panid
      display: "",
      num: "",
      cart: [],
      order: [],
      searchbar: '',
    }
  },
  methods: {
    addToCart(product) {
      const naaNa = this.cart.find(item => item.id === product.id);
      if (!naaNa) {
        this.cart.push({ ...product });
        alert('✅ Gidugang sa Cart!');
      } else {
        alert('⚠️ Naa na ni sa Cart!');
      }
    },

    removeFromCart(id) {
      this.cart = this.cart.filter(item => item.id !== id)
    },

    addToOrder(products) {
      const items = Array.isArray(products) ? products : [products];
      items.forEach(item => {
        this.order.push({ ...item, orderDate: new Date().toLocaleDateString() });
      });
      this.cart = [];
      this.currentPage = 'showOrder';
      alert('🎉 Order Successful!');
    },

    submitProduct(product){
      this.addToCart(product);
      this.closeAddModal();
    },

    closeAddModal() {
      this.showaddModal = false;
    },

    changePage(page) {
      console.log('Gibalhin sa:', page); // Makita nimo sa console
      this.currentPage = page;
    },

    handleSearch(search) {
      this.searchbar = search;
    }
  }
}
</script>