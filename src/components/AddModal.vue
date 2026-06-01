<template>
    <div
        class="flex items-center flex-col justify-center h-screen fixed top-0 inset-0 bg-black/60 backdrop-blur-sm z-50">
        <div
            class="group w-80 bg-gray-200 dark:bg-gray-800 h-[280px] shadow-xl rounded-2xl overflow-hidden transition-all duration-300 hover:shadow-2xl">
            <div class="flex justify-center flex-col items-center p-5">
                <input v-model="brandImage" type="text" placeholder="Image Link"
                    class="mb-3 p-2.5 border border-gray-300 dark:border-gray-600 rounded-lg w-full text-center bg-white dark:bg-gray-700 text-gray-800 dark:text-white focus:outline-none focus:ring-2 focus:ring-blue-500 transition-colors">
                <input v-model="brandName" type="text" placeholder="Product Name"
                    class="mb-3 p-2.5 border border-gray-300 dark:border-gray-600 rounded-lg w-full text-center bg-white dark:bg-gray-700 text-gray-800 dark:text-white focus:outline-none focus:ring-2 focus:ring-blue-500 transition-colors">
                <input v-model="brandPrice" type="text" placeholder="Price"
                    class="mb-4 p-2.5 border border-gray-300 dark:border-gray-600 rounded-lg w-full text-center bg-white dark:bg-gray-700 text-gray-800 dark:text-white focus:outline-none focus:ring-2 focus:ring-blue-500 transition-colors">
                <div class="gap-4 flex w-full justify-center">
                    <button @click="closeaddModal"
                        class="border p-2 px-5 cursor-pointer hover:scale-105 duration-300 bg-red-500 hover:bg-red-600 text-white rounded-lg font-medium shadow-sm hover:shadow-md">
                        Cancel
                    </button>
                    <button @click="submitProduct"
                        class="border p-2 px-5 cursor-pointer hover:scale-105 duration-300 bg-green-500 hover:bg-green-600 text-white rounded-lg font-medium shadow-sm hover:shadow-md">
                        Submit
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            brandName: '',
            brandImage: '',
            brandPrice: ''
        };
    },
    methods: {
        closeaddModal() {
            this.$emit('close');
        },
        submitProduct() {
            this.$emit('submitProduct', {
                name: this.brandName,
                image: this.brandImage,
                price: this.brandPrice
            });
        }
    }
};
</script>