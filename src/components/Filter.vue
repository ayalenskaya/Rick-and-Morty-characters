<template>
  <div class="filter-container">
    <input v-model="filter.name" type="text" placeholder="Filter by name" />
    <select v-model="filter.status">
      <option value="">All</option>
      <option value="alive">Alive</option>
      <option value="dead">Dead</option>
      <option value="unknown">Unknown</option>
    </select>
    <button @click="applyFilters">Apply</button>
  </div>
</template>
