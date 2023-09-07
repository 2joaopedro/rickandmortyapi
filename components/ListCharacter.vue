<script setup>
 const character = defineProps(["image","name", "status", "species"])
</script>
<template>
   <div className="w-72 min-h-[10rem] bg-white text-gray-700 shadow-lg rounded-2xl overflow-hidden ">
        <img :src="character.image" alt="" className="w-full  object-cover"/>
    <div class="p-5 flex-col">
        <div className="py-5 flex-col gap-">
            <h1 className="font-bold text-2xl">{{ character.name }}</h1>
            <div className="flex gap-5">
                <span className="font-medium text-base">{{ character.status }}</span>
                <span className="font-medium text-base">{{ character.species }}</span>
            </div>
        </div>
    </div>
   </div>
</template>