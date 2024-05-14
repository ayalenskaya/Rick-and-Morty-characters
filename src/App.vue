<template>
  <div class="character-container">
    <h1>Rick and Morty Characters</h1>
    <Filter @applyFilters="applyFilters" />
    <div class="character-grid">
      <CharacterCard v-for="character in characters" :key="character.id" :character="character" />
    </div>
    <Pagination :page="page" :totalPages="totalPages" @nextPage="nextPage" @prevPage="prevPage" />
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import Filter from "@/components/Filter.vue";
import CharacterCard from "@/components/CharacterCard.vue";
import Pagination from "@/components/Pagination.vue";

const characters = ref([]);
const page = ref(1);
const totalPages = ref(1);
const filter = ref({
  name: "",
  status: ""
});

const fetchCharacters = async () => {
  try {
    const response = await fetch(
      `https://rickandmortyapi.com/api/character?page=${page.value}&name=${filter.value.name}&status=${filter.value.status}`
    );
    const data = await response.json();
    characters.value = data.results;
    totalPages.value = data.info.pages;
  } catch (error) {
    console.error("Error fetching characters:", error);
  }
};

const nextPage = () => {
  if (page.value < totalPages.value) {
    page.value++;
    fetchCharacters();
  }
};

const prevPage = () => {
  if (page.value > 1) {
    page.value--;
    fetchCharacters();
  }
};

const applyFilters = (appliedFilter) => {
  page.value = 1;
  filter.value = appliedFilter;
  fetchCharacters();
};

onMounted(fetchCharacters);
</script>

