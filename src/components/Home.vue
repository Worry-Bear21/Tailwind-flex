<template>
    <div class="bg-gray-200 w-screen p-8 sm:p-16 dark:bg-gray-900">
        <div class="p-4 mb-4 text-lg text-center leading-tight first-letter:capitalize font-medium dark:text-gray-100">
        </div>
        <div class="mx-auto w-fit grid grid-cols-1 lg:grid-cols-3 sm:grid-cols-2 gap-6">
            <div v-for="(product, i) in products" :key="product.id"
                class="group bg-gray-200 h-[400px] shadow-lg rounded-2xl overflow-hidden">
                <img class="w-full h-60 object-cover hover:cursor-pointer hover:scale-105 duration-300 mt-5"
                    :src="product.image" alt="product image" />
                <div class="flex justify-center relative">
                    <div class="flex flex-col">
                        <p class="hover:text-yellow-500 cursor-pointer font-semibold">{{ product.name }}</p>
                        <p>{{ product.price }}</p>
                        <div class="flex justify-center gap-2">
                            <button
                                class="border px-3 rounded-lg bg-gray-400 hover:scale-105 duration-300 cursor-pointer">{{
                                    product.btn1 }}</button>
                            <button
                                class="border px-3 rounded-lg bg-orange-400 hover:scale-105 duration-300 cursor-pointer">{{
                                    product.btn2 }}</button>
                            <button
                                class="border px-3 rounded-lg bg-yellow-400 hover:scale-105 duration-300 cursor-pointer">{{
                                    product.btn3 }}</button>
                        </div>
                    </div>

                    <button @click="handleBuy(i)"
                        class="text-xl text-gray-900 cursor-pointer hover:scale-105 duration-300 hover:bg-red-500 hover:text-black flex absolute p-2 px-2 justify-center items-center text-center mt-20 border rounded-xl bg-green-500">
                        {{ product.option }}
                    </button>
                </div>
            </div>
        </div>

        <Modal v-if="showProductModal" :selectedProduct="products[currentIndex]" @close="closeProductModal" />
        <AddModal v-if="addingProduct" @close="closeaddModal" @submitProduct="add" />
        <Addtocart v-if="currentpage === 'showCart'" />

    </div>
</template>


<script>
import Addtocart from './Addtocart.vue';
import Modal from './Modal.vue'
import AddModal from './AddModal.vue'

export default {
    components: { Modal, AddModal, Addtocart },
    props: {
        addingProduct: {
            type: Boolean,

        }
    },
    data() {
        return {
            currentIndex: 0,
            showProductModal: false,
            products: [
                {
                    id: 1,
                    image: 'https://cdn.csgoskins.gg/public/uih/items/aHR0cHM6Ly9jZG4uY3Nnb3NraW5zLmdnL3B1YmxpYy9pbWFnZXMvYnVja2V0cy9lY29uL2RlZmF1bHRfZ2VuZXJhdGVkL3dlYXBvbl9jejc1YV9hbV9yb3lhbF9saWdodC41ZmFkNDM5Y2RlMTcyMDYwNWNhOTEzMDliNmVjZjhkNTBiMjNlMjQzLnBuZw--/auto/auto/85/notrim/bd85bf60019dee42ab78d1545ef352a4.webp',
                    name: 'CZ75-Auto | Chalice',
                    color: 'bg-white',
                    option: 'add-to-cart',
                    price: '$639.99',
                    btn1: 'SMG',
                    btn2: 'Light',
                    btn3: 'B-tier'
                },
                {
                    id: 2,
                    image: 'https://cdn.csgoskins.gg/public/uih/items/aHR0cHM6Ly9jZG4uY3Nnb3NraW5zLmdnL3B1YmxpYy9pbWFnZXMvYnVja2V0cy9lY29uL2RlZmF1bHRfZ2VuZXJhdGVkL3dlYXBvbl9jejc1YV9nc19jel9zbmFrZXNfcHVycGxlX2xpZ2h0LjZhN2VhYmE2NzkwY2Y2YTFlZTlmNTgwOWRkOWI0MjBiOTUwMmRmMGUucG5n/auto/auto/85/notrim/ff55d8e577b2e603da9e90f4b2fbf5c2.webp',
                    name: 'CZ75-Auto | Xiangliu',
                    color: 'bg-white',
                    option: 'add-to-cart',
                    price: '$505.99',
                    btn1: 'SMG',
                    btn2: 'Light',
                    btn3: 'B-tier'
                },
                {
                    id: 3,
                    image: 'https://cdn.csgoskins.gg/public/uih/items/aHR0cHM6Ly9jZG4uY3Nnb3NraW5zLmdnL3B1YmxpYy9pbWFnZXMvYnVja2V0cy9lY29uL2RlZmF1bHRfZ2VuZXJhdGVkL3dlYXBvbl9jejc1YV9oeWVfcGFpc2xleV9kZXNhdF9saWdodC5lY2UzOWVjZTAxNjQxNTNhMjU4NWE4Y2Q4M2NjM2JlZGRiYzgyYjI0LnBuZw--/auto/auto/85/notrim/2f5128238d482ac3a7488c779d5ba19e.webp',
                    name: 'R-99 SMG',
                    color: 'bg-white',
                    option: 'add-to-cart',
                    price: '$639.99',
                    btn1: 'SMG',
                    btn2: 'Light',
                    btn3: 'B-tier'
                },
                {
                    id: 4,
                    image: 'https://cdn.csgoskins.gg/public/uih/items/aHR0cHM6Ly9jZG4uY3Nnb3NraW5zLmdnL3B1YmxpYy9pbWFnZXMvYnVja2V0cy9lY29uL2RlZmF1bHRfZ2VuZXJhdGVkL3dlYXBvbl9tYWMxMF9tYWMxMF90cmFpbl9jcmFzaF9saWdodC42MzYxYmU0NWExN2IyZTMxMjc5ZWRkZjFhNTY1M2QwMzk0YzYyMGZmLnBuZw--/auto/auto/85/notrim/445b19568b78b256cdaecbf89cd17d7a.webp',
                    name: 'G7 Scout',
                    color: 'bg-white',
                    option: 'add-to-cart',
                    price: '$639.99',
                    btn1: 'DMR',
                    btn2: 'Light',
                    btn3: 'B-tier'
                },
                {
                    id: 5,
                    image: 'https://cdn.csgoskins.gg/public/uih/items/aHR0cHM6Ly9jZG4uY3Nnb3NraW5zLmdnL3B1YmxpYy9pbWFnZXMvYnVja2V0cy9lY29uL2RlZmF1bHRfZ2VuZXJhdGVkL3dlYXBvbl9tYWMxMF9jdV9tYWMxMF9uZW9ucmlkZXJfbGlnaHQuNWFhODgwODI3NDczYWJjYzA4NjgxZDMxNGI5NTg5MTc3ZjAyMzQzMS5wbmc-/auto/auto/85/notrim/ed87907e9b8d1f327f0cfab1875436c0.webp',
                    name: 'Neon Rider',
                    color: 'bg-white',
                    option: 'add-to-cart',
                    price: '$639.99',
                    btn1: 'Marksman',
                    btn2: 'Energy',
                    btn3: 'B-tier'
                },
                {
                    id: 6,
                    image: 'https://cdn.csgoskins.gg/public/uih/items/aHR0cHM6Ly9jZG4uY3Nnb3NraW5zLmdnL3B1YmxpYy9pbWFnZXMvYnVja2V0cy9lY29uL2RlZmF1bHRfZ2VuZXJhdGVkL3dlYXBvbl9tYWMxMF9jdV9tYWMxMF9uYWNyZV9saWdodC4wN2Q1NTdlOGRjMjc5OGY2MzUzNWU0NGNmMGY3NjdlNDdhNTFlNDVlLnBuZw--/auto/auto/85/notrim/d895b01fe87000c4e6b74e75405e5bc8.webp',
                    name: 'Disco Tech',
                    color: 'bg-white',
                    option: 'add-to-cart',
                    price: '$639.99',
                    btn1: 'Sniper',
                    btn2: 'Energy',
                    btn3: 'B-tier'
                },
                {
                    id: 7,
                    image: 'https://cdn.csgoskins.gg/public/uih/items/aHR0cHM6Ly9jZG4uY3Nnb3NraW5zLmdnL3B1YmxpYy9pbWFnZXMvYnVja2V0cy9lY29uL2RlZmF1bHRfZ2VuZXJhdGVkL3dlYXBvbl9tYWMxMF9jdV9tYWMxMF9yZWRob3RfbGlnaHQuYWI0NDAxN2ZjZmI4NTBmMTllODNhMGQ5MDVlYmE3NzY4YmY4MDVkNS5wbmc-/auto/auto/85/notrim/b7db1f16d97b81919b394d4e67e4e65b.webp',
                    name: 'Heat',
                    color: 'bg-white',
                    option: 'add-to-cart',
                    price: '$639.99',
                    btn1: 'Sniper Rifle',
                    btn2: 'Supply Drop',
                    btn3: 'A-tier'
                }
                
            ]
        }
    },
    methods: {
        handleBuy(i) {
            this.showProductModal = true;
            this.currentIndex = i;
        },
        closeProductModal() {
            this.showProductModal = false;
        },
        closeaddModal() {
            this.$emit('close')
        },
        add(newProduct) {
            this.products.push(...newProduct)
        }
    }
};
</script>
