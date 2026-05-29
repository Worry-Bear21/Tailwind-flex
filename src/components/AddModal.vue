<template>
    <div class="flex items-center flex-col justify-center h-screen fixed top-0 inset-0 bg-black/50 z-50">
        <div class="group w-80 bg-gray-200 h-[260px] shadow-lg rounded-2xl overflow-hidden">
            <div class="flex justify-center flex-col items-center p-4">
                <input v-model="brandImage" type="text" placeholder="Image Link"
                    class="mb-2 p-2 border rounded w-full text-center">
                <input v-model="brandName" type="text" placeholder="Product Name"
                    class="mb-2 p-2 border rounded w-full text-center">
                <input v-model="brandPrice" type="text" placeholder="Price"
                    class="mb-2 p-2 border rounded w-full text-center">
                <div class="gap-5 flex">
                    <button @click="closeaddModal"
                        class="mt-4 border p-2 px-4 cursor-pointer hover:scale-105 duration-300 bg-green-500 rounded-xl hover:bg-red-500 hover:text-white">Buy
                        now</button>
                    <button @click="submitProduct"
                        class="mt-4 border p-2 px-4 cursor-pointer hover:scale-105 duration-300 bg-green-500 rounded-xl hover:bg-red-500 hover:text-white">Submit
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