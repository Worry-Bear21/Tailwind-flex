<template>
    <div class="bg-white w-[420px] p-5 rounded-sm shadow-lg border border-gray-100">
        <p class="text-sm text-gray-700 font-medium mb-3">Download the App for the best experience</p>
        <div class="flex gap-4 mb-4">
            <div class="w-[120px] h-[120px] bg-gray-100 flex items-center justify-center">
                <img src="https://api.qrserver.com/v1/create-qr-code/?size=120x120&data=https://lazada.com.ph" alt="QR Code" />
            </div>
            <div class="text-sm text-blue-500 cursor-pointer  space-y-1">
                <p class="hover:scale-105 hover:duration-300 ">• Shop through our app to enjoy:</p>
                <p class="hover:scale-105 hover:duration-300 ">• Exclusive Vouchers</p>
                <p class="hover:scale-105 hover:duration-300 ">• Better deals</p>
                <p class="hover:scale-105 hover:duration-300 ">• Personalised recommendations</p>
                <p class="hover:scale-105 hover:duration-300 ">• Find out first</p>
            </div>
        </div>
        <div class="flex mb-3">
            <input type="text" placeholder="eg. 0123456789" class="flex-1 border border-gray-300 px-3 py-1.5 text-sm rounded-l-sm focus:outline-none" />
            <button class="bg-orange-500 text-white px-3 rounded-r-sm">➔</button>
        </div>
        <div class="flex gap-3 justify-center">
            <img src="https://static.vecteezy.com/system/resources/previews/049/734/879/non_2x/get-it-on-google-play-download-on-the-app-store-logo-banner-illustration-free-vector.jpg" alt="App Store" class="h-20 w-full" />
        </div>
    </div>
</template>

<script>
export default {
    name: 'Savemore'
};
</script>