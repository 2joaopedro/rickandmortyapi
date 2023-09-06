<script setup>
 import Logo from "../assets/Logo.svg"
</script>

<template>
    <header as="nav" className="flex items-center justify-between flex mx-40 my-5">
        <img :src="Logo" alt="" class="w-14 h-14"/>
        <div>
           <ul className="flex gap-5">
            <li><NuxtLink to="/">Home</NuxtLink></li>
            <li><NuxtLink to="/Character">Character</NuxtLink></li>
            <li><NuxtLink to="/Location">Location</NuxtLink></li>
            <li><NuxtLink to="/Episode">Episode</NuxtLink></li>
           </ul>
        </div>
        <div>
            <input placeholder="Search"/>
        </div>
    </header>
</template>

<Style lang="scss"></Style>