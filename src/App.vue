<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'

import { ref } from 'vue';
const orderObject = ref({ user: 1, view: 2 });
const viewExpand = ref(true);
const userExpand = ref(false);

function toggleView() {
  if (orderObject.value.view === 2) {
    viewExpand.value = !viewExpand.value;
  }
  userExpand.value = false;
}

function toggleUser() {
  if (orderObject.value.user === 2) {
    userExpand.value = !userExpand.value;
  }
  viewExpand.value = false;
}

function togglePosition(name) {
  if (name === "user") {
    if (orderObject.value.user !== 2) {
      orderObject.value.user = 2;
      orderObject.value.view = 1;
      viewExpand.value = false;
    }
  }
  if (name === "view") {
    if (orderObject.value.view !== 2) {
      orderObject.value.view = 2;
      orderObject.value.user = 1;
      userExpand.value = false;
    }
  }
}


</script>

<template>
  <!-- Layout start -->
  <div class="flex">
    <!-- Left side menu start -->
    <div class="min-h-screen h-full menu">
      <img src="./assets/logo.svg" class="h-16 w-16 mx-auto mt-16 mb-12" alt="" />
      <ul class="list-none pl-12 menu-list">
        <li class="text-white text-2xl font-semibold flex rounded-tl-3xl rounded-bl-3xl relative menu-item cursor-pointer active ">
          <div class="p-2 bg-red-800 rounded-full mr-8">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor"
            class="w-6 h-6 stroke-2">
              <path stroke-linecap="round" stroke-linejoin="round"
              d="M2.25 12l8.954-8.955c.44-.439 1.152-.439 1.591 0L21.75 12M4.5 9.75v10.125c0 .621.504 1.125 1.125 1.125H9.75v-4.875c0-.621.504-1.125 1.125-1.125h2.25c.621 0 1.125.504 1.125 1.125V21h4.125c.621 0 1.125-.504 1.125-1.125V9.75M8.25 21h8.25" />
            </svg>
          </div>
          <span>Home</span>
        </li>
      </ul>
    </div>
    <!-- Left side menu end -->

    <div class="dashboard">
      <!-- TOp navbar start -->
      <div class="px-8 py-4 rounded-br-2xl drop-shadow navbar">
        <div class="flex items-center justify-end cursor-pointer">
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
      <!-- Top navbar end -->
      <!-- main area start-->
      <div class="p-8">
        <div class="flex flex-col gap-6 relative">
          <!-- User container start -->
          <div class="border border-red-700 rounded-3xl absolute w-full transition-all duration-1000 ease-linear" :class="[orderObject.user===2?'top-16': 'top-0']">
            <button class="bg-red-700 text-white w-full py-2 px-4 font-semibold text-xl flex items-center justify-between rounded-tl-3xl rounded-tr-3xl" :class="[userExpand?'':'rounded-bl-3xl rounded-br-3xl']" @click="togglePosition('user')">
              <h4 class="basis-1/2 text-right">User</h4>
              <div class="basis-1/2">
                <Transition name="fade">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6 ml-auto" @click="toggleUser" v-if="!userExpand">
                  <path fill-rule="evenodd" d="M12.53 16.28a.75.75 0 01-1.06 0l-7.5-7.5a.75.75 0 011.06-1.06L12 14.69l6.97-6.97a.75.75 0 111.06 1.06l-7.5 7.5z" clip-rule="evenodd" />
                </svg>
                </Transition>
              </div>
            </button>
            <Transition name="userCollapseExpand">
              <div class="bg-white rounded-bl-3xl rounded-br-3xl view-box" v-if="userExpand">
                <div class="bg-red-300 pt-2 view-box-content">
                  <h5 class="text-xl font-bold text-gray-700 underline text-decoration-solid underline-offset-4 px-2">User Content</h5>
                </div>
                <div class="p-4 view-box-content">
                  <h2 class="text-4xl text-center text-gray-700 mt-20 mb-4 font-bold">User</h2>

                  <p class="text-gray-700 text-xl">
                    <h5 class="text-black text-semibold text-2xl">What is Lorem Ipsum?</h5>
                    Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.
                  </p>

                  
                </div>
              </div>
            </Transition>
          </div>
          <!-- User container end -->
          <!-- View container start -->
          <div class="border border-red-700 rounded-3xl absolute w-full transition-all duration-1000 ease-linear" :class="[orderObject.view===2?'top-16': 'top-0']">
            <button class="bg-red-700 text-white w-full py-2 px-4 font-semibold text-xl flex items-center justify-between rounded-tl-3xl rounded-tr-3xl" :class="[viewExpand?'':'rounded-bl-3xl rounded-br-3xl']"   @click="togglePosition('view')">
              <h4 class="basis-1/2 text-right">View</h4>
              <div class="basis-1/2">
                <Transition name="fade">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6 ml-auto" @click="toggleView" v-if="!viewExpand">
                  <path fill-rule="evenodd" d="M12.53 16.28a.75.75 0 01-1.06 0l-7.5-7.5a.75.75 0 011.06-1.06L12 14.69l6.97-6.97a.75.75 0 111.06 1.06l-7.5 7.5z" clip-rule="evenodd" />
                </svg>
                </Transition>
              </div>
            </button>
            <Transition name="viewCollapseExpand">
              <div class="bg-white rounded-bl-3xl rounded-br-3xl view-box" v-if="viewExpand">
                <div class="bg-red-300 pt-2 view-box-content">
                  <h5 class="text-xl font-bold text-gray-700 underline text-decoration-solid underline-offset-4 px-2">View Content</h5>
                </div>
                <div class="p-4 view-box-content">
                  <h2 class="text-4xl text-center text-gray-700 mb-4 font-bold">View</h2>

                  <p class="text-gray-700 text-xl">
                    <h5 class="text-black text-semibold text-2xl">What is Lorem Ipsum?</h5>
                    Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.
                  </p>

                  <p class="text-gray-700 text-xl mt-10">
                    <h5 class="text-black text-semibold text-2xl">Why do we use it?</h5>
                      It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters, as opposed to using 'Content here, content here', making it look like readable English. Many desktop publishing packages and web page editors now use Lorem Ipsum as their default model text, and a search for 'lorem ipsum' will uncover many web sites still in their infancy. Various versions have evolved over the years, sometimes by accident, sometimes on purpose (injected humour and the like).
                  </p>

                  <p class="text-gray-700 text-xl mt-10">
                    <h5 class="text-black text-semibold text-2xl">Why do we use it?</h5>
                      It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters, as opposed to using 'Content here, content here', making it look like readable English. Many desktop publishing packages and web page editors now use Lorem Ipsum as their default model text, and a search for 'lorem ipsum' will uncover many web sites still in their infancy. Various versions have evolved over the years, sometimes by accident, sometimes on purpose (injected humour and the like).
                  </p>
                </div>
              </div>
            </Transition>

          </div>
          <!-- View container end -->
        </div>
        
      </div>
      <!-- main area end-->
    </div>
  </div>
  <!-- Layout end -->
</template>

<style lang="scss">
body{
  background-color: #393E46;
}
.menu{
  
  background-color: #171D26;
  width: 100px;
  transition: width 0.7s linear;
  &:hover {
    width: 250px;
    .menu-list {
      span {
          opacity: 1;
        }
    }
  }
  .menu-list {
    span{
      opacity: 0;
      transition: all 0.3s linear;
    }
    .active {
      background-color: #393E46;

      ::after,
      ::before{
        content: "";
        height: 40px;
        width: 40px;
        position: absolute;
        background: none;
        border-radius: 50%;
        right: 0;
      }

      ::before{
        top: -40px;
        box-shadow: 17px 17px 0px -2px #393E46;
      }

      ::after{
        bottom: -40px;
        box-shadow: 17px -17px 0px -2px #393E46;
      }
    }
  }
}
// .menu:hover{
//   width: 250px;
// }
.dashboard {
  width: 100%;
  .navbar {
    background-color: #171D26;
  }
}

.view-box{
  min-height: 100%;
  height: auto;
  opacity: 1;
}

.viewCollapseExpand-enter-active,
.viewCollapseExpand-leave-active,
.userCollapseExpand-enter-active,
.userCollapseExpand-leave-active,
.fade-enter-active,
.fade-leave-active {
  transition: all 1s linear;
}
  
.viewCollapseExpand-enter-from,
.viewCollapseExpand-leave-to,
.userCollapseExpand-enter-from,
.userCollapseExpand-leave-to,
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  min-height: 0;
}
</style>
