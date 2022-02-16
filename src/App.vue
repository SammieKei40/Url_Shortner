<template>
  <div class="relative md:block">
    <nav class="bg-white md:py-4 py-2">
      <div class="flex justify-around items-center">
        <a href="" class="flex"><h1 class="font-bold text-3xl self-center whitespace-nowrap">Shortly</h1></a>
        <i class="fa-solid fa-bars text-gray-500 text-3xl md:hidden lg:hidden cursor-pointer" @click="toggleNav()"></i>

        
        <div class=" bg-gray-500 rounded flex-col p-4 md:p-0 md:flex absolute md:relative left-0 md:top-0 top-10 md:bg-white lg:bg-white w-full md:flex-row justify-start items-center lg:w-auto " :class="openNav ? 'flex': 'hidden'">
          <hr class="bg-white"/>
          <a href="/about" class=" text-white lg:text-gray-500 md:text-black hover:text-green-500 font-bold my-4 md:my-0 m-auto mx-6"
            >Features</a>
            
          <a
            href="/"
            class=" text-white lg:text-gray-500 md:text-black hover:text-green-500 font-bold mb-4 md:mb-0 mx-auto md:mx-6"
            >Pricing</a
          >
    
          <a href="/" class=" text-white lg:text-gray-500 md:text-black hover:text-green-500 font-bold mb-4 md:mb-0 md:mx-auto mx-6"
            >Resources</a
          >
      
          <div class="ml-2 lg:ml-20 flex-col md:flex-row md:w-auto flex justify-center">
            <div class="grid justify-center">
               <button type="button" class="text-white lg:text-gray-500 bg-green-300    lg:hover:bg-green-300 hover:text-white transition ease-in-out delay-150 hover:scale-110 hover:bg-gray-300 duration-300  font-bold rounded-full px-5 py-2.5 text-center mr-3">Login</button>
            </div>
            <div class="grid justify-center mt-2 md:mt-0">
              <button type="button" class="text-white lg:text-gray-500 bg-green-300    lg:hover:bg-green-300 hover:text-white  font-bold rounded-full px-5 py-2.5 text-center mr-3 transition ease-in-out delay-150 hover:scale-110 hover:bg-gray-300 duration-300">Signup</button>
            </div>
          </div>
        </div>
      </div>

    </nav>
    <div class="mt-0 md:mt-0">
    <Hero/>
    <Input/>
    <HomePage/>
    <Footer />
    </div>
  </div>
</template>

<script setup lang="ts">
import Hero from "./components/Hero.vue";
import HomePage from "./components/HomePage.vue";
import Footer from "./components/Footer.vue";
import Input from "./components/Input.vue";
import { ref } from '@vue/reactivity'

let openNav = ref(false)
function toggleNav() {
  openNav.value = !openNav.value
}
</script>

<style>
*{
  font-family: 'Poppins', sans-serif;
}
</style>