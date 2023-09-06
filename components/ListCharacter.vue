<script setup>
 const character = defineProps(["image","name", "status", "species"])
</script>
<template>
   <div className="flex items-center gap-5 bg-gray-600 rounded-2xl">
    <div>
        <img :src="character.image" alt="" className="w-52 h-52 rounded-s-2xl"/>
    </div>
    <div class="flex flex-col gap-5">
        <div className="flex flex-col">
            <h1>{{ character.name }}</h1>
            <div className="flex gap-5">
                <p>{{ character.status }}</p>
                <p>{{ character.species }}</p>
            </div>
        </div>

        <div className="flex flex-col">
            <h1>{{ character.name }}</h1>
            <div className="flex gap-5">
                <p>{{ character.status }}</p>
                <p>{{ character.species }}</p>
            </div>
        </div>
    </div>
   </div>
</template>