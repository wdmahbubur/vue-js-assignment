<script setup>
defineProps({
    orderObject: {
        required: true
    },
    userExpand: {
        required: true
    },
    toggleUser: {
        required: true
    },
    togglePosition: {
        required: true
    }

})
</script>

<template>
    <div class="border border-red-700 rounded-3xl absolute w-full transition-all duration-1000 ease-linear"
        :class="[orderObject.user===2?'top-16': 'top-0']">
        <button
            class="bg-red-700 text-white w-full py-2 px-4 font-semibold text-xl flex items-center justify-between rounded-tl-3xl rounded-tr-3xl"
            :class="[userExpand?'':'rounded-bl-3xl rounded-br-3xl']" @click="togglePosition('user')">
            <h4 class="basis-1/2 text-right">User</h4>
            <div class="basis-1/2">
                <Transition name="fade">
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6 ml-auto"
                        @click="toggleUser" v-if="!userExpand">
                        <path fill-rule="evenodd"
                            d="M12.53 16.28a.75.75 0 01-1.06 0l-7.5-7.5a.75.75 0 011.06-1.06L12 14.69l6.97-6.97a.75.75 0 111.06 1.06l-7.5 7.5z"
                            clip-rule="evenodd" />
                    </svg>
                </Transition>
            </div>
        </button>
        <Transition name="userCollapseExpand">
            <div class="bg-white rounded-bl-3xl rounded-br-3xl view-box" v-if="userExpand">
                <div class="bg-red-300 pt-2 view-box-content">
                    <h5 class="text-xl font-bold text-gray-700 underline text-decoration-solid underline-offset-4 px-2">User
                        Content</h5>
                </div>
                <div class="p-4 view-box-content">
                    <h2 class="text-4xl text-center text-gray-700 mt-20 mb-4 font-bold">User</h2>
    
                    <p class="text-gray-700 text-lg">
                    <h5 class="text-black text-semibold text-2xl">What is Lorem Ipsum?</h5>
                    Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the
                    industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and
                    scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap
                    into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the
                    release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing
                    software like Aldus PageMaker including versions of Lorem Ipsum.
                    </p>
    
    
                </div>
            </div>
        </Transition>
    </div>
</template>