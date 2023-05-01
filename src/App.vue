<template>
  <div class="soda-list">
    <div class="soda-header">
      <h1 class="soda-heading">Soda Companies</h1>
    </div>
    <div class="soda-container">
      <div class="soda-names">
        <div v-for="soda in sodas" :key="soda.id" @click="selectSoda(soda)">
          <div :class="{'soda-box': true, 'active': soda === selectedSoda}">
            <p>{{ soda.companyName }}</p>
          </div>
        </div>
      </div>
      <div class="soda-details">
        <h2 v-if="!selectedSoda">Click on a company name to view details</h2>
        <soda-item v-if="selectedSoda" :soda="selectedSoda" />
      </div>
    </div>
    <div class="author-container">
      <p class="author">Created by Sai Krishna Chejarla</p>
    </div>
  </div>
</template>

<script>

import SodaItem from './components/SodaItem.vue';

export default {
  components: {
    SodaItem,
  },
  data() {
    return {
      sodas: [],
      selectedSoda: null,
      
    };
  },
  mounted() {
    fetch('https://saikrishna-wad-final.herokuapp.com/api')
      .then(response => response.json())
      .then(data => {
        this.sodas = data.sodas;
      })
      .catch(error => {
        console.error(error);
      });
  },
  methods: {
    selectSoda(soda) {
      this.selectedSoda = soda;
    },
  },
};
</script>



<style>
.soda-list {
  background-color: #f2f2f2;
  display: flex;
  flex-direction: column;
  height: 100vh;
}

.soda-header {
  background-color: #D51C23;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 10%;
}

.soda-heading {
  font-size: 3rem;
  font-weight: bold;
  margin: 0;
}

.soda-container {
  display: flex;
  flex-direction: row;
  flex-grow: 1;
  align-items: center;
  justify-content: space-between;
  padding: 30px;
}

.soda-names {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.soda-box {
  width: 200px;
  height: 80px;
  border: 1px solid #D51C23;
  border-radius: 8px;
  margin: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  background-color: white;
  transition: background-color 0.3s ease;
}

.soda-box:hover {
  background-color: #D51C23;
  color: white;
}

.soda-box p {
  font-size: 1.5rem;
  font-weight: bold;
  margin: 0;
}

.active {
  background-color: lightgray;
}

.soda-details {
  width: 50%;
  margin-left: 40px;
}

.author-container {
  background-color: #D51C23;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 10%;
}

.author {
  margin: 0;
  font-size: 1.2rem;
  font-style: italic;
}
</style>