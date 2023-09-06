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
    <main>
        <div className="m-10 grid grid-cols-1 gap-x-6 gap-y-8 sm:grid-cols-2 lg:grid-cols-3 xl:gap-x-8">
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