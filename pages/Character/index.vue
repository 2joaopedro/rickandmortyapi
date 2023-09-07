<script setup>
 
 let characters = reactive(ref())

 onMounted(() => {
    fetch("https://rickandmortyapi.com/api/character")
    .then(response => response.json())
    .then(response =>  {
        characters.value = response.results
        console.log(response)
    })
 })
</script>

<template>
    <main class="flex  justify-center min-w-full ">
        <div class="my-28 grid grid-cols-1 gap-x-5 gap-y-5 sm:grid-cols-2 lg:grid-cols-3 xl:gap-x-5">
            <ListCharacter 
                v-for="character in characters" 
                :key="character.id" 
                :name="character.name" 
                :status="character.status" 
                :species="character.species"
                :image="character.image"
                >
            </ListCharacter>
        </div>
    </main>
</template>