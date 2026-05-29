<<template>
  <div>
    <NavBar @openAddModal="showAddModal" @goTo="changePage" :cart="cart" />

    <Home v-if="currentPage === 'home'" :addingProduct="showaddModal" @close="closeAddModal" @addTocart="addToCart" />
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
      }
    }
  }
</script>