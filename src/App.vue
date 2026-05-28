<template>
  <div>
    <NavBar @openAddModal="showAddModal" @goTo="changePage" />

    <Home v-if="currentPage === 'home'" :addingProduct="showaddModal" @close="closeAddModal" />
    <Addtocart v-if="currentPage === 'showCart'" :addingProduct="showaddModal"  />
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
      currentPage: 'home'
    }
  },
  methods: {
    showAddModal() {
      this.showaddModal = true;
    },
    closeAddModal() {
      this.showaddModal = false;
    },
    changePage(page) {
      this.currentPage = page;
    }
  }
}
</script>