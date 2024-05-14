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

