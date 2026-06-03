<template>
    <div class="bg-gray-100 dark:bg-gray-900 w-full min-h-screen pt-24 px-4 sm:px-8 lg:px-16">
        <div class="max-w-5xl mx-auto py-10">
            <h1 class="text-2xl text-gray-800 dark:text-white font-bold mb-6">Order History</h1>

            <div v-if="orderlist.length === 0" class="text-gray-500 dark:text-gray-400 text-center py-10">
                <p>Wala pa kay nahimo nga order.</p>
            </div>

            <div v-for="(order, index) in orderlist" :key="index" class="bg-gray-800 rounded-lg p-4 mb-4 shadow">
                <div class="flex justify-between items-center border-b border-gray-700 pb-3">
                    <span class="px-3 py-1 text-sm rounded-full bg-green-100 text-gray-700">Delivered</span>
                </div>

                <div class="mt-4 space-y-3">
                    <div class="flex items-center">
                        <img :src="order.image" alt="Product" class="w-16 h-16 rounded mr-4">
                        <div>
                            <p class="font-medium text-white">{{ order.name }}</p>
                            <p class="text-sm text-gray-400">Qty: 1</p>
                        </div>
                        <p class="ml-auto font-semibold text-gray-300">{{ order.price }}</p>
                    </div>

                </div>

                <div class="mt-4 flex justify-between items-center border-t pt-3">
                    <p class="text-gray-400">Total: <span class="font-bold">₱5,697.00</span></p>
                    <a href="#" class="text-blue-600 hover:underline text-sm">View Invoice</a>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        orderlist: {
            type: Array,
            default: () => []
        }
    }
}
</script>