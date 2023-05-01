<template>
  <div>
    <h2>{{ soda.companyName }}</h2>
    <p>Tasting Notes: {{ soda.tastingNotes }}</p>
    <p>Best Before: {{ soda.bestBefore }}</p>
    <p>History: {{ soda.history }}</p>
    <p>Average Selling Cost: {{ soda.averageSellingCost }}</p>
  </div>
</template>

<script>
export default {
  props: ['soda'],
};
</script>
