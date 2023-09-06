<script setup>
 const character = defineProps(["name", "status", "species"])
</script>
<template>
   <div>
    <div></div>
    <div>
        <div>
            <h1>{{ character.name }}</h1>
            <p>{{ character.status }}</p>
            <p>{{ character.species }}</p>
        </div>
    </div>
   </div>
</template>