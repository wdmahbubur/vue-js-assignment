<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
</script>

<template>
  <!-- Layout start -->
  <div class="grid grid-cols-12">
    <!-- Left side menu start -->
    <div class="col-span-2 h-screen menu">
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
          Home
        </li>
      </ul>
    </div>
    <!-- Left side menu end -->

    <div class="col-span-10">
      <!-- TOp navbar start -->
      <div class="px-8 py-4 rounded-br-2xl navbar">
        <div class="flex items-center justify-end cursor-pointer">
          <div class="bg-red-800 p-2 h-10 w-10 rounded-full">
            <svg xmlns="http://www.w3.org/2000/svg" fill="#000" viewBox="0 0 24 24" stroke-width="1.5" stroke="none"
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
        <div class="">

        </div>
        <!-- User container start -->
        <div>

        </div>
        <!-- User container end -->
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
  .menu-list {
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
.navbar {
  background-color: #171D26;
}
</style>
