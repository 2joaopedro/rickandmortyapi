<script setup>
 const character = defineProps(["image","name", "status", "species"])
 const StatusColor = character.status === "Alive" ? "bg-green-400" : "bg-red-400"
</script>
<template>
   <div class="w-72 min-h-[10rem] bg-white text-gray-700 shadow-lg rounded-2xl overflow-hidden cursor-pointer transition ease-in-out delay-150 hover:-translate-y-2 hover:scale-100 hover:shadow-lg duration-200 ">
        <img :src="character.image" alt="" class="w-full  object-cover"/>
    <div class="p-5 flex-col items-center justify-center">
        <div class="py-10 flex-col items-center max-w-[25rem]">
            <h1 class="font-bold text-2xl">{{ character.name }}</h1>
            <div class="flex items-center gap-5">
                <div class="flex  items-center gap-2">
                    <div :class="StatusColor" class="w-2 h-2 rounded-full"></div>
                    <p class="font-medium text-base">{{ character.status }}</p>
                </div>
                <p class="font-medium text-base">{{ character.species }}</p>
            </div>
        </div>
    </div>
   </div>
</template>