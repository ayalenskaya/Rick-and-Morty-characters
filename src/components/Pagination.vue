<template>
    <div class="pagination">
      <button @click="prevPage" :disabled="page <= 1">Previous</button>
      <button @click="nextPage" :disabled="page >= totalPages">Next</button>
    </div>
  </template>
  
