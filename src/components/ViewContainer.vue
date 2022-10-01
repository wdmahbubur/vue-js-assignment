<script setup>
defineProps({
    orderObject: {
        required: true
    },
    viewExpand: {
        required: true
    },
    toggleView:{
        required: true
    },
    togglePosition: {
        required: true
    }
    
})

</script>
<template>
    <div class="border border-red-700 rounded-3xl absolute w-full transition-all duration-1000 ease-linear"
        :class="[orderObject.view===2?'top-16': 'top-0']">
        <button
            class="bg-red-700 text-white w-full py-2 px-4 font-semibold text-xl flex items-center justify-between rounded-tl-3xl rounded-tr-3xl"
            :class="[viewExpand?'':'rounded-bl-3xl rounded-br-3xl']" @click="togglePosition('view')">
            <h4 class="basis-1/2 text-right">View</h4>
            <div class="basis-1/2">
                <Transition name="fade">
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6 ml-auto"
                        @click="toggleView" v-if="!viewExpand">
                        <path fill-rule="evenodd"
                            d="M12.53 16.28a.75.75 0 01-1.06 0l-7.5-7.5a.75.75 0 011.06-1.06L12 14.69l6.97-6.97a.75.75 0 111.06 1.06l-7.5 7.5z"
                            clip-rule="evenodd" />
                    </svg>
                </Transition>
            </div>
        </button>
        <Transition name="viewCollapseExpand">
            <div class="bg-white rounded-bl-3xl rounded-br-3xl view-box" v-if="viewExpand">
                <div class="bg-red-300 pt-2 view-box-content">
                    <h5 class="text-xl font-bold text-gray-700 underline text-decoration-solid underline-offset-4 px-2">View
                        Content</h5>
                </div>
                <div class="p-4 view-box-content">
                    <h2 class="text-4xl text-center text-gray-700 mb-4 font-bold">View</h2>

                    <p class="text-gray-700 text-lg">
                    <h5 class="text-black text-semibold text-2xl">What is Lorem Ipsum?</h5>
                    Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the
                    industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and
                    scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap
                    into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the
                    release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing
                    software like Aldus PageMaker including versions of Lorem Ipsum.
                    </p>

                    <p class="text-gray-700 text-lg mt-10">
                    <h5 class="text-black text-semibold text-2xl">Why do we use it?</h5>
                    It is a long established fact that a reader will be distracted by the readable content of a page when
                    looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution
                    of letters, as opposed to using 'Content here, content here', making it look like readable English. Many
                    desktop publishing packages and web page editors now use Lorem Ipsum as their default model text, and a
                    search for 'lorem ipsum' will uncover many web sites still in their infancy. Various versions have
                    evolved over the years, sometimes by accident, sometimes on purpose (injected humour and the like).
                    </p>

                    <p class="text-gray-700 text-lg mt-10">
                    <h5 class="text-black text-semibold text-2xl">Why do we use it?</h5>
                    It is a long established fact that a reader will be distracted by the readable content of a page when
                    looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution
                    of letters, as opposed to using 'Content here, content here', making it look like readable English. Many
                    desktop publishing packages and web page editors now use Lorem Ipsum as their default model text, and a
                    search for 'lorem ipsum' will uncover many web sites still in their infancy. Various versions have
                    evolved over the years, sometimes by accident, sometimes on purpose (injected humour and the like).
                    </p>
                </div>
            </div>
        </Transition>
    </div>
</template>