<script setup>
// import 
import { onMounted, ref } from 'vue';
import Navbar from './components/Navbar.vue';
import SideMenu from './components/SideMenu.vue';
import ViewContainer from './components/ViewContainer.vue';
import UserContainer from './components/UserContainer.vue';

// state
const responsiveMenuExpand = ref(true);
const orderObject = ref({ user: 1, view: 2 });
const viewExpand = ref(true);
const userExpand = ref(false);

// methods
function responsiveMenuToggle(){
  responsiveMenuExpand.value = !responsiveMenuExpand.value;
}

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

onMounted(() => {
  window.addEventListener('resize', function () {
    if (this.window.innerWidth<=576) {
      responsiveMenuExpand.value = false;
    }
    if (this.window.innerWidth > 576) {
      responsiveMenuExpand.value = true;
    }
  })
})

</script>

<template>
  <!-- Layout start -->
  <div class="flex">
         
    <!-- Left side menu start -->
      <SideMenu :responsiveMenuExpand="responsiveMenuExpand" :responsiveMenuToggle="responsiveMenuToggle"/>
      <!-- Left side menu end -->
  
      <div class="dashboard pb-4">
      <!-- Top navbar start -->
        <Navbar :responsiveMenuToggle="responsiveMenuToggle"/>
      <!-- Top navbar end -->
      <!-- main area start-->
      <div class="p-8">
        <div class="relative">
          <!-- User container start -->
            <UserContainer :orderObject="orderObject" :userExpand="userExpand" :toggleUser="toggleUser" :togglePosition="togglePosition" />
          <!-- User container end -->
          <!-- View container start -->
            <ViewContainer :orderObject="orderObject" :viewExpand="viewExpand" :toggleView="toggleView" :togglePosition="togglePosition"/>
          <!-- View container end --> 
          <div></div>
        </div>
        
      </div>
      <!-- main area end-->
    </div>
  </div>
  <!-- Layout end -->
</template>
