<script setup>
defineProps({
    responsiveMenuToggle: {
        required: true,
    }
})
</script>

<template>
    <div class="px-2 py-4 rounded-br-2xl drop-shadow navbar">
        <div class="flex items-center justify-between md:justify-end">
            <div class="md:hidden cursor-pointer" @click="responsiveMenuToggle">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="#fff"
                    class="w-10 h-10">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5" />
                </svg>
            </div>
            <div class="flex items-center cursor-pointer">
                <div class="bg-red-800 p-2 h-10 w-10 rounded-full">
                <svg xmlns="http://www.w3.org/2000/svg" fill="#fff" viewBox="0 0 24 24" stroke-width="1.5" stroke="none"
                    class="w-6 h-6">
                    <path stroke-linecap="round" stroke-linejoin="round"
                        d="M15.75 6a3.75 3.75 0 11-7.5 0 3.75 3.75 0 017.5 0zM4.501 20.118a7.5 7.5 0 0114.998 0A17.933 17.933 0 0112 21.75c-2.676 0-5.216-.584-7.499-1.632z" />
                </svg>
                </div>
                <h4 class="text-white font-semibold text-xl ml-2">Demo User</h4>
            </div>
        </div>
    </div>
</template>



<style scoped>

</style>