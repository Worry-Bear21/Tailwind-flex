<template>
    <div class="bg-gray-200 w-full min-h-screen p-8 sm:p-16 dark:bg-gray-900 mt-25">
        <div class="max-w-5xl mx-auto p-6">
            <h1 class="text-2xl text-gray-200 font-bold mb-6">Order History</h1>

            <!-- Order Card -->
            <div v-for="order in orders" class=" shadow rounded-lg p-4 mb-4" style="background-color: #1a202c;">
                <div class="flex justify-between items-center border-b pb-3">
                    <div>
                        <p class="text-sm font-semibold text-white">Order #10234</p>
                        <p class="font-semibold text-white">Placed on: Jan 15, 2026</p>
                    </div>
                    <span
                        class="px-3 py-1 text-md rounded-full bg-green-100 text-gray-700 cursor-pointer hover:scale-105 duration-300">
                        Delivered
                    </span>
                </div>

                <div class="mt-4 space-y-3">
                    <div class="flex items-center">
                        <img :src="order.image"
                            alt="Product" class="w-16 h-16 rounded mr-4">
                        <div>
                            <p class="font-medium text-white">{{ order.name }}</p>
                            <p class="text-sm text-gray-400">Qty: 1</p>
                        </div>
                        <p class="ml-auto font-semibold text-gray-400">{{ order.price }}</p>
                    </div>

                    <div class="flex items-center">
                        <img src="https://cdn.csgoskins.gg/public/uih/items/aHR0cHM6Ly9jZG4uY3Nnb3NraW5zLmdnL3B1YmxpYy9pbWFnZXMvYnVja2V0cy9lY29uL2RlZmF1bHRfZ2VuZXJhdGVkL3dlYXBvbl9nM3NnMV9jdV9nM3NnMV90YWN0aWNhbG1hcF9saWdodC5lNmFkZjAwNWFjYjVlMTY1NzIwOThjMDExYmIyZmViNWY3OWEyMjk0LnBuZw--/auto/auto/85/notrim/4ebf5b79bafb6c5df585e49f76d2bb11.webp"
                            alt="Product" class="w-16 h-16 rounded mr-4">
                        <div>
                            <p class="font-medium text-white">Bluetooth Speaker</p>
                            <p class="text-sm text-gray-400">Qty: 2</p>
                        </div>
                        <p class="ml-auto font-semibold text-gray-400">₱3,198.00</p>
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
        orders: {
            type: Array,

        }
    },
}
</script>