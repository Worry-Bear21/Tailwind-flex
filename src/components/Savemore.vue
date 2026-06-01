<template>
    <div
        class="bg-white w-[420px] p-5 rounded-xl shadow-lg border border-gray-100 hover:shadow-2xl transition-all duration-300 hover:-translate-y-1">
        <p class="text-sm text-gray-800 font-bold mb-4">Download the App for the best experience</p>

        <div class="flex gap-4 mb-4 items-start">
            <div
                class="w-[120px] h-[120px] bg-gray-50 rounded-lg shadow-sm flex items-center justify-center overflow-hidden border border-gray-200">
                <img src="https://api.qrserver.com/v1/create-qr-code/?size=120x120&data=https://lazada.com.ph"
                    alt="QR Code to download Lazada App"
                    class="w-full h-full object-contain hover:scale-105 transition-transform duration-500" />
            </div>

            <div class="text-sm text-gray-600 space-y-2 mt-1">
                <p class="flex items-center gap-2 hover:translate-x-1 transition-transform duration-300 font-medium">
                    ✨ Shop through our app to enjoy:
                </p>
                <p class="flex items-center gap-2 hover:translate-x-1 transition-transform duration-300">• Exclusive
                    Vouchers</p>
                <p class="flex items-center gap-2 hover:translate-x-1 transition-transform duration-300">• Better deals
                </p>
                <p class="flex items-center gap-2 hover:translate-x-1 transition-transform duration-300">• Personalised
                    recommendations</p>
                <p class="flex items-center gap-2 hover:translate-x-1 transition-transform duration-300">• Find out
                    first</p>
            </div>
        </div>

        <div class="flex mb-4 rounded-lg overflow-hidden shadow-sm">
            <input type="text" placeholder="e.g. 0123456789"
                class="flex-1 border border-gray-300 px-3 py-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-orange-500 focus:border-orange-500 transition-all" />
            <button
                class="bg-gradient-to-r from-orange-500 to-orange-600 hover:from-orange-600 hover:to-orange-700 text-white px-5 transition-all duration-200 font-medium text-base">
                ➔
            </button>
        </div>

        <div class="flex justify-center items-center pt-1">
            <img src="https://static.vecteezy.com/system/resources/previews/049/734/879/non_2x/get-it-on-google-play-download-on-the-app-store-logo-banner-illustration-free-vector.jpg"
                alt="Download on App Store and Google Play"
                class="h-16 w-auto object-contain hover:scale-105 transition-transform duration-300 cursor-pointer" />
        </div>
    </div>
</template>

<script>
export default {
    name: 'Savemore'
};
</script>