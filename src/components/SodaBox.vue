<template>
    <div class="soda-box" :class="{ 'selected': isSelected }" @mouseover="isHovered = true" @mouseleave="isHovered = false" @click="$emit('show-soda-details', soda)">
      {{ soda.companyName }}
    </div>
  </template>
  
  <script>
  export default {
    props: ['soda'],
    data() {
      return {
        isHovered: false,
      };
    },
    computed: {
      isSelected() {
        return this.isHovered || this.soda.isSelected;
      },
    },
  };
  </script>
  
  <style>
  .soda-box {
    border: 1px solid gray;
    padding: 10px;
    margin: 10px;
    cursor: pointer;
    transition: background-color 0.3s ease;
    text-align: center;
  }
  
  .soda-box.selected {
    background-color: gray;
    color: white;
  }
  
  
  @media screen and (max-width: 768px) {
    .soda-box {
      width: 100%;
    }
  }
  </style>
  