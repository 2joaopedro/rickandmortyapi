<template>
  <main class="flex justify-center min-w-full">
    <div class="my-28">
      <div class="flex gap-5">
        <input  
          type="search"
          v-model="searchTerm"
          placeholder="Search..."
          class="w-full p-3 mb-4 bg-white text-gray-700 shadow-md rounded-2xl"
        />
        <div class="flex gap-5 items-center sm:flex-row">
          <select id="pages" v-model="selectedPages" class="max-w-md p-3 mb-4 bg-white text-gray-700 shadow-md rounded-2xl">
            <option selected value="1">Page 1</option>
            <option value="2">Page 2</option>
            <option value="3">Page 3</option>
            <option value="4">Page 4</option>
            <option value="5">Page 5</option>
            <option value="6">Page 6</option>
            <option value="7">Page 7</option>
            <option value="8">Page 8</option>
            <option value="9">Page 9</option>
            <option value="10">Page 10</option>
          </select>

          <select id="status" v-model="selectedStatus" class="max-w-md p-3 mb-4 bg-white text-gray-700 shadow-md rounded-2xl">
            <option value="">Choose a Status</option>
            <option value="Alive">Alive</option>
            <option value="Dead">Dead</option>
          </select>

          <select id="species" v-model="selectedSpecies" class="max-w-md p-3 mb-4 bg-white text-gray-700 shadow-md rounded-2xl">
            <option value="">Choose a Species</option>
            <option value="Human">Human</option>
            <option value="Alien">Alien</option>
            <option value="Animal">Animal</option>
            <option value="Robot">Robot</option>
            <option value="Humanoid">Humanoid</option>
            <option value="Disease">Disease</option>
            <option value="Cronenberg">Cronenberg</option>
            <option value="Mythological Creature">Mythological Creature</option>
          </select>
        </div>
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
import { ref, reactive, onMounted, computed, watch } from 'vue';

let characterList = reactive(ref([]));
const searchTerm = ref('');
const selectedStatus = ref('');
const selectedSpecies = ref('');
const selectedPages = ref('1'); // Inicialize a página selecionada com '1'

onMounted(async () => {
  fetchData();
});

watch(selectedPages, () => {
  fetchData();
});

async function fetchData() {
  try {
    const response = await fetch(`https://rickandmortyapi.com/api/character?page=${selectedPages.value}`);
    const data = await response.json();
    characterList.value = data.results;
  } catch (error) {
    console.error("Error fetching data:", error);
  }
}

const filteredCharacters = computed(() => {
  return characterList.value.filter((character) => {
    const nameMatch = character.name.toLowerCase().includes(searchTerm.value.toLowerCase());
    const statusMatch = !selectedStatus.value || character.status === selectedStatus.value;
    const speciesMatch = !selectedSpecies.value || character.species === selectedSpecies.value;
    return nameMatch && statusMatch && speciesMatch;
  });
});
</script>
