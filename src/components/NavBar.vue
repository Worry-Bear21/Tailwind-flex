<template>
  <div class="bg-gray-100">
    <nav class="fixed top-0 left-0 right-0 z-50 bg-white bg-opacity-90 backdrop-blur-md">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex items-center justify-between h-16">
          <div class="flex-shrink-0">
            <a href="/" class="text-black font-bold text-2xl">
              <svg class="h-6 w-auto" viewBox="0 0 342 35" xmlns="http://www.w3.org/2000/svg">
                <path
                  d="M0 .1a9.7 9.7 0 0 0 7 7h11l.5.1v27.6h6.8V7.3L26 7h11a9.8 9.8 0 0 0 7-7H0zm238.6 0h-6.8v34.8H263a9.7 9.7 0 0 0 6-6.8h-30.3V0zm-52.3 6.8c3.6-1 6.6-3.8 7.4-6.9l-38.1.1v20.6h31.1v7.2h-24.4a13.6 13.6 0 0 0-8.7 7h39.9v-21h-31.2v-7h24zm116.2 28h6.7v-14h24.6v14h6.7v-21h-38zM85.3 7h26a9.6 9.6 0 0 0 7.1-7H78.3a9.6 9.6 0 0 0 7 7zm0 13.8h26a9.6 9.6 0 0 0 7.1-7H78.3a9.6 9.6 0 0 0 7 7zm0 14.1h26a9.6 9.6 0 0 0 7.1-7H78.3a9.6 9.6 0 0 0 7 7zM308.5 7h26a9.6 9.6 0 0 0 7-7h-40a9.6 9.6 0 0 0 7 7z"
                  fill="currentColor"></path>
              </svg>
            </a>
          </div>

          <div class="flex items-center space-x-4">
            <a href="#"
              class="text-sm font-medium text-gray-900 hover:text-gray-600 px-3 py-2 rounded-md transition-colors duration-300">Model
              S</a>
            <a href="#"
              class="text-sm font-medium text-gray-900 hover:text-gray-600 px-3 py-2 rounded-md transition-colors duration-300">Model
              3</a>
            <a href="#"
              class="text-sm font-medium text-gray-900 hover:text-gray-600 px-3 py-2 rounded-md transition-colors duration-300">Model
              X</a>
            <a href="#"
              class="text-sm font-medium text-gray-900 hover:text-gray-600 px-3 py-2 rounded-md transition-colors duration-300">Model
              Y</a>
            <a href="#"
              class="text-sm font-medium text-gray-900 hover:text-gray-600 px-3 py-2 rounded-md transition-colors duration-300">Solar
              Roof</a>
            <a href="#"
              class="text-sm font-medium text-gray-900 hover:text-gray-600 px-3 py-2 rounded-md transition-colors duration-300">Solar
              Panels</a>

            <a href="#" @click="navigate('home')"
              class="text-sm font-medium text-gray-900 hover:text-gray-600 px-3 py-2 rounded-md transition-colors duration-300">Shop</a>

            <svg @click="navigate('showCart')" class="w-6 h-6 text-red-500 cursor-pointer hover:scale-105 duration-300"
              aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor"
              viewBox="0 0 24 24">
              <path fill-rule="evenodd"
                d="M4 4a1 1 0 0 1 1-1h1.5a1 1 0 0 1 .979.796L7.939 6H19a1 1 0 0 1 .979 1.204l-1.25 6a1 1 0 0 1-.979.796H9.605l.208 1H17a3 3 0 1 1-2.83 2h-2.34a3 3 0 1 1-4.009-1.76L5.686 5H5a1 1 0 0 1-1-1Z"
                clip-rule="evenodd" />
            </svg>

            <a @click="addModal" href="#"
              class="text-sm font-medium text-gray-900 hover:text-gray-600 px-3 py-2 rounded-md transition-colors duration-300">Add</a>
          </div>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  methods: {
    addModal() {
      this.$emit('openAddModal')
    },
    navigate(page) {
      this.$emit('goTo', page)
    }
  }
}
</script>