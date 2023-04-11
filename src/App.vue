<template>
  <div>
    il y a {{ result }} facon de faire {{ total }} avec {{ numberOfDices }} de {{ numberOfFace }}
  </div>
</template>
  
<script setup lang="ts">
import { ref } from 'vue';

const numberOfDices = ref<number>(2);
const numberOfFace = ref<number>(6);
const total = ref<number>(7);
const result = ref<number>(0);

function getTotalPossibleConfigurations(total: number, numberOfDices: number, numberOfFace: number): number {
  const res = 0;
  console.log("t", total, "nb", numberOfDices, "faces", numberOfFace);
  return res;
}

result.value = getTotalPossibleConfigurations(7, numberOfDices.value, numberOfFace.value);

defineExpose({ result, numberOfDices, numberOfFace });
</script>

<style scoped>
</style>
