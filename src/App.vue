<template>
  <div>

    <NavBar @openAddModal="showAddModal" @goTo="changePage" @search="handleSearch" :cart="cart" />


    <Home v-if="currentPage === 'home'" :addingProduct="showaddModal" :searchbar="searchbar" @close="closeAddModal"
      @addTocart="addToCart" @addToorder="addToOrder" />

    <Addtocart v-if="currentPage === 'showCart'" :cartitems="cart"  @addToorder="addToOrder"  />
    <Order v-if="currentPage === 'showOrder'" :orderlist="order" />
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue'
import Home from './components/Home.vue'
import Addtocart from './components/Addtocart.vue';
import Order from './components/Order.vue';


export default {
  components: { NavBar, Home, Addtocart, Order },

  data() {
    return {
      showaddModal: false,
      currentPage: 'home',
      display: "0",
      num: "",
      cart: [],
      searchbar: '',
      order: [],

    }
  },
  methods: {
    addToOrder(product) {
      this.order.push({ ...product })
    },
    addToCart(product) {
      this.cart.push({ ...product })
    },
    showAddModal() {
      this.showaddModal = true;
    },
    closeAddModal() {
      this.showaddModal = false;
    },
    changePage(page) {
      this.currentPage = page;
    },

    handleSearch(search) {
      this.searchbar = search;
    }
  }
}
</script>