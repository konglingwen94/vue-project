<template>
    <div>
      <button @click="toggleModal" v-if="!showModal" class="open-button">Open Modal</button>
      
      <!-- Simple Modal with Overlay -->
      <div v-show="showModal" class="overlay">
        <div class="modal">
          <button @click="toggleModal" class="close-button">&times;</button>
          <h3>Simple Modal</h3>
          <p>This is a simple modal.</p>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const showModal = ref(false);
  
  const toggleModal = () => {
    showModal.value = !showModal.value;
  };
  </script>
  
  <style scoped>
  .overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.6);
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .modal {
    background: white;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
    position: relative;
    width: 300px;
  }
  
  .close-button {
    background: none;
    border: none;
    font-size: 24px;
    position: absolute;
    top: 10px;
    right: 10px;
    cursor: pointer;
  }
  
  .open-button {
    position: fixed;
    top: 20px;
    right: 20px;
    background: #007bff;
    color: white;
    border: none;
    padding: 10px;
    cursor: pointer;
    border-radius: 4px;
  }
  </style>