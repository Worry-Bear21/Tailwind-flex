<template>
    <div class=" w-[350px] p-5 rounded-sm shadow-lg border border-gray-100" style="background-color: #1a202c;">
        <div class="flex gap-4 mb-4">

            <div class="text-sm text-gray-200 cursor-pointer  space-y-1">
                <svg @click="confirmAndClose" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" aria-hidden="true"
                    role="img" width="25" height="25" viewBox="0 0 24 24" class="flex ml-70">
                    <g fill="currentColor" fill-rule="evenodd" clip-rule="evenodd">
                        <path
                            d="M5.47 5.47a.75.75 0 0 1 1.06 0l12 12a.75.75 0 1 1-1.06 1.06l-12-12a.75.75 0 0 1 0-1.06">
                        </path>
                        <path
                            d="M18.53 5.47a.75.75 0 0 1 0 1.06l-12 12a.75.75 0 0 1-1.06-1.06l12-12a.75.75 0 0 1 1.06 0">
                        </path>
                    </g>
                </svg>
                <div class="flex gap-5">
                    <svg class=" text-gray-400 hover:text-orange-500" aria-hidden="true"
                        xmlns="http://www.w3.org/2000/svg" width="64" height="64" fill="currentColor"
                        viewBox="0 0 24 24">
                        <path d="M16 10c0-.55228-.4477-1-1-1h-3v2h3c.5523 0 1-.4477 1-1Z" />
                        <path
                            d="M13 15v-2h2c1.6569 0 3-1.3431 3-3 0-1.65685-1.3431-3-3-3h-2.256c.1658-.46917.256-.97405.256-1.5 0-.51464-.0864-1.0091-.2454-1.46967C12.8331 4.01052 12.9153 4 13 4h7c.5523 0 1 .44772 1 1v9c0 .5523-.4477 1-1 1h-2.5l1.9231 4.6154c.2124.5098-.0287 1.0953-.5385 1.3077-.5098.2124-1.0953-.0287-1.3077-.5385L15.75 16l-1.827 4.3846c-.1825.438-.6403.6776-1.0889.6018.1075-.3089.1659-.6408.1659-.9864v-2.6002L14 15h-1ZM6 5.5C6 4.11929 7.11929 3 8.5 3S11 4.11929 11 5.5 9.88071 8 8.5 8 6 6.88071 6 5.5Z" />
                        <path
                            d="M15 11h-4v9c0 .5523-.4477 1-1 1-.55228 0-1-.4477-1-1v-4H8v4c0 .5523-.44772 1-1 1s-1-.4477-1-1v-6.6973l-1.16797 1.752c-.30635.4595-.92722.5837-1.38675.2773-.45952-.3063-.5837-.9272-.27735-1.3867l2.99228-4.48843c.09402-.14507.2246-.26423.37869-.34445.11427-.05949.24148-.09755.3763-.10887.03364-.00289.06747-.00408.10134-.00355H15c.5523 0 1 .44772 1 1 0 .5523-.4477 1-1 1Z" />
                    </svg>

                    <p class="hover:scale-105 hover:duration-300 text-lg mt-5 hover:text-orange-500 ">Help Center</p>
                </div>
                <div class="flex gap-5">
                    <svg class=" text-gray-400 hover:text-orange-500" aria-hidden="true"
                        xmlns="http://www.w3.org/2000/svg" width="64" height="64" fill="currentColor"
                        viewBox="0 0 24 24">
                        <path fill-rule="evenodd"
                            d="M4 4a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V6a2 2 0 0 0-2-2H4Zm10 5a1 1 0 0 1 1-1h3a1 1 0 1 1 0 2h-3a1 1 0 0 1-1-1Zm0 3a1 1 0 0 1 1-1h3a1 1 0 1 1 0 2h-3a1 1 0 0 1-1-1Zm0 3a1 1 0 0 1 1-1h3a1 1 0 1 1 0 2h-3a1 1 0 0 1-1-1Zm-8-5a3 3 0 1 1 6 0 3 3 0 0 1-6 0Zm1.942 4a3 3 0 0 0-2.847 2.051l-.044.133-.004.012c-.042.126-.055.167-.042.195.006.013.02.023.038.039.032.025.08.064.146.155A1 1 0 0 0 6 17h6a1 1 0 0 0 .811-.415.713.713 0 0 1 .146-.155c.019-.016.031-.026.038-.04.014-.027 0-.068-.042-.194l-.004-.012-.044-.133A3 3 0 0 0 10.059 14H7.942Z"
                            clip-rule="evenodd" />
                    </svg>
                    <p class="hover:scale-105 hover:duration-300 text-lg mt-5 hover:text-orange-500">Orders & Payment
                    </p>
                </div>
                <div class="flex gap-5">
                    <svg class="text-gray-400 hover:text-orange-500" xmlns="http://www.w3.org/2000/svg"
                        xmlns:xlink="http://www.w3.org/1999/xlink" aria-hidden="true" role="img" width="64" height="64"
                        viewBox="0 0 24 24">
                        <g fill="none" stroke="currentColor" stroke-linecap="round" stroke-width="1.5">
                            <path stroke-linejoin="round" stroke-miterlimit="1.5"
                                d="M8 19a2 2 0 1 0 0-4a2 2 0 0 0 0 4m10 0a2 2 0 1 0 0-4a2 2 0 0 0 0 4" />
                            <path d="M10.05 17H15V6.6a.6.6 0 0 0-.6-.6H1m4.65 11H3.6a.6.6 0 0 1-.6-.6v-4.9" />
                            <path stroke-linejoin="round" d="M2 9h4" />
                            <path
                                d="M15 9h5.61a.6.6 0 0 1 .548.356l1.79 4.028a.6.6 0 0 1 .052.243V16.4a.6.6 0 0 1-.6.6h-1.9M15 17h1" />
                        </g>
                    </svg>
                    <p class="hover:scale-105 hover:duration-300 text-lg mt-5 hover:text-orange-500">Shipping & Delivery
                    </p>
                </div>
                <div class="flex gap-5">
                    <svg class="text-gray-400 hover:text-orange-500" xmlns="http://www.w3.org/2000/svg"
                        xmlns:xlink="http://www.w3.org/1999/xlink" aria-hidden="true" role="img" width="64" height="64"
                        viewBox="0 0 24 24">
                        <path fill="currentColor" d="M21 10v9a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-9z" opacity=".3"></path>
                        <path fill="currentColor"
                            d="M20 3a2 2 0 0 1 2 2v3H2V5a2 2 0 0 1 2-2zm-6 10h-4a1 1 0 1 0 0 2h4a1 1 0 1 0 0-2"></path>
                    </svg>
                    <p class="hover:scale-105 hover:duration-300 text-lg mt-5 hover:text-orange-500">Returns & Funds</p>
                </div>

            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CustomModal',
    methods: {
        confirmAndClose() {
            this.closeModal();
        }
    }

};
</script>