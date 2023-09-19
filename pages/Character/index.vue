<template>
    <main class="flex justify-center min-w-full">
      <div class="my-28 ">
       <div>
        <input  
        type="search"
        v-model="searchTerm"
        placeholder="Search..."
        class="w-full p-3 mb-4 bg-white text-gray-700 shadow-md rounded-2xl " />
       </div>
  
        <div class="grid grid-cols-1 gap-x-5 gap-y-5 sm:grid-cols-2 lg:grid-cols-3 xl:gap-x-5">
          <CardCharacter
            v-for="character in filteredCharacters"
            :key="character.id"
            :name="character.name"
            :status="character.status"
            :species="character.species"
            :image="character.image"
          >
          </CardCharacter>
        </div>
      </div>
    </main>
  </template>
  
  <script setup>
  import { ref, reactive, onMounted, computed } from 'vue';
  
  let characters = reactive(ref([]));
  const searchTerm = ref('');
  
  onMounted(async () => {
    try {
      const response = await fetch("https://rickandmortyapi.com/api/character");
      const data = await response.json();
      characters.value = data.results;
    } catch (error) {
      console.error("Error fetching data:", error);
    }
  });
  
  const filteredCharacters = computed(() => {
    return characters.value.filter((character) => {
      return character.name.toLowerCase().includes(searchTerm.value.toLowerCase());
    });
  });
  </script>
  