<template>
    <div>
      <button @click="toggleSidebar" v-if="!showSidebar" class="open-button">Open Sidebar</button>
      
      <!-- Sidebar Modal with Overlay -->
      <div v-if="showSidebar" class="overlay">
        <div class="sidebar-modal">
          <div class="sidebar-content">
            <button @click="toggleSidebar" class="close-button">&times;</button>
            <h3>Related Videos</h3>
            <ul>
              <li v-for="(video, index) in relatedVideos" :key="index">
                {{ video.title }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const relatedVideos = ref([
    { title: 'Video 1' },
    { title: 'Video 2' },
    { title: 'Video 3' }
  ]);
  
  const showSidebar = ref(false);
  
  const toggleSidebar = () => {
    showSidebar.value = !showSidebar.value;
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
    justify-content: flex-end;
    align-items: center;
  }
  
  .sidebar-modal {
    width: 600px;
    height: 100%;
    background: rgba(255, 255, 255, 0.9);
    box-shadow: -2px 0 5px rgba(0, 0, 0, 0.5);
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    padding: 20px;
    transition: transform 0.3s ease;
    transform: translateX(0);
  }
  
  .sidebar-content {
    width: 100%;
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