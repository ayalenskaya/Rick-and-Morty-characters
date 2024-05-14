<template>
    <div class="character-card">
      <div class="character-content">
        <img :src="character.image" :alt="character.name" class="character-image" />
        <div class="character-details">
          <h2>{{ character.name }}</h2>
          <p>{{ character.status }} - {{ character.species }}</p>
          <p>Last known location: {{ character.origin.name }}</p>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  const props = defineProps({
    character: Object
  });
  </script>
  
