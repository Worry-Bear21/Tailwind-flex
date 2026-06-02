<template>
  <div>

    <NavBar @openAddModal="showAddModal" @goTo="changePage" @search="handleSearch" :cart="cart" />


    <Home v-if="currentPage === 'home'" :addingProduct="showaddModal" :searchbar="searchbar"
      @close="closeAddModal" @addTocart="addToCart" />

    <Addtocart v-if="currentPage === 'showCart'" :cartitems="cart" />
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue'
import Home from './components/Home.vue'
import Addtocart from './components/Addtocart.vue';

export default {
  components: { NavBar, Home, Addtocart },

  data() {
    return {
      showaddModal: false,
      currentPage: 'home',
      display: "0",
      num: "",
      cart: [],
      searchbar:''
      
    }
  },
  methods: {
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