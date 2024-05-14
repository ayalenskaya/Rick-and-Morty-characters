<template>
    <div class="pagination">
      <button @click="prevPage" :disabled="page <= 1">Previous</button>
      <button @click="nextPage" :disabled="page >= totalPages">Next</button>
    </div>
  </template>
  
  <script setup>
  import { defineProps, defineEmits } from "vue";
  
  const props = defineProps({
    page: Number,
    totalPages: Number
  });
  
  const emit = defineEmits(["nextPage", "prevPage"]);
  
  const nextPage = () => {
    if (props.page < props.totalPages) {
      emit("nextPage");
    }
  };
  
  const prevPage = () => {
    if (props.page > 1) {
      emit("prevPage");
    }
  };
  </script>
  
  <style scoped>
  .pagination {
    display: flex;
    justify-content: center;
    gap: 10px;
  }
  </style>
  