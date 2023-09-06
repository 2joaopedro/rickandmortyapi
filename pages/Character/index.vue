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
    <main  className="lex mx-40 my-5">
        <ListCharacter 
            v-for="character in characters" 
            :key="character.id" 
            :name="character.name" 
            :status="character.status" 
            :species="character.species">
        </ListCharacter>
    </main>
</template>