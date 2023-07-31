<script setup lang="ts">
  import Badge from '../src/components/Badge.vue'
  import Dice from '../src/components/Dice.vue'
</script>

<template>
  <!-- navbar -->
  <!-- resume official / resume Character sheet -->
  <!-- Cover Letter official / cover letter in chartacter sheet-->
  <!-- Dice roll? -->
  <Badge /> 
  <div class="diceContainer"><Dice /></div>
  
</template>

<style scoped>
.diceContainer {
  display: flex;
  justify-content: center; /* Center horizontally */
  align-items: center; /* Center vertically */
  height: 50vh; /* Set the container to full viewport height */
}
</style>
