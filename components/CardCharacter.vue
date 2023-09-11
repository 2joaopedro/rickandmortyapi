<script setup>
 const character = defineProps(["image","name", "status", "species"])
</script>
<template>
   <div class="w-72 min-h-[10rem] bg-white text-gray-700 shadow-lg rounded-2xl overflow-hidden ">
        <img :src="character.image" alt="" class="w-full  object-cover"/>
    <div class="p-5 flex-col items-center justify-center">
        <div class="py-10 flex-col max-w-[25rem]">
            <h1 class="font-bold text-2xl">{{ character.name }}</h1>
            <div class="flex gap-5">
                <span class="font-medium text-base">{{ character.status }}</span>
                <span class="font-medium text-base">{{ character.species }}</span>
            </div>
        </div>
        <button class="bg-sky-700 p-2 rounded-md text-white font-bold hover:bg-sky-800">Sobre mais</button>
    </div>
   </div>
</template>