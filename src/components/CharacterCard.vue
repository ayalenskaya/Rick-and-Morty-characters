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
  
  <style scoped>
  .character-card {
    width: clamp(300px, 80%, 500px); 
    display: flex;
    background: rgb(60, 62, 68);
    border-radius: 0.5rem;
    box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 6px -1px, rgba(0, 0, 0, 0.06) 0px 2px 4px -1px;
  }
  
  .character-content {
    display: flex;
    align-items: center;
  }
  
  .character-details {
    padding: 1rem;
    text-align: left;
  }

  @media screen and (max-width: 670px) {
  .character-content {
    flex-direction: column;
    width: 100%;
  }
  .character-card {
    justify-content: center;
  }

}
  </style>
  