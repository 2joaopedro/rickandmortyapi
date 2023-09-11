<script setup>
 import Logo from "../assets/Logo.svg"
</script>

<template>
    <header as="nav" class="flex fixed z-20  items-center justify-between bg-white shadow-xl min-w-full  px-60 py-2">
        <img :src="Logo" alt="" class="w-14 h-14"/>
        <div class="flex items-center space-x-5 text-base">
            <NuxtLink to="/" class="text-lg font-semibold">Home</NuxtLink>
            <NuxtLink to="/Character" class="text-lg font-semibold">Character</NuxtLink>
        </div>
    </header>
</template>

