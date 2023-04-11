<template>
  <div>
    il y a {{ resultat }} facon de faire {{ total }} avec {{ numberOfDices }} dés de {{ numberOfFace }} faces
  </div>
</template>
  
<script setup lang="ts">
import { ref } from 'vue';

const numberOfDices = ref<number>(2);
const numberOfFace = ref<number>(6);
const total = ref<number>(7);
const resultat = ref<number>(0);


/*>===================== FUNCTION FOR 2 DICES*/
function getTotalPossibleConfigurations(total: number, numberOfDices: number, numberOfFace: number): number {
  let res = 0;

  console.log("t", total, "nb", numberOfDices, "faces", numberOfFace);
  for (let faceDice1 = 1; faceDice1 <numberOfFace+1; faceDice1++) {
    for (let faceDice2 = 1; faceDice2 <numberOfFace+1; faceDice2++) {
      console.log("dés 1", faceDice1);
      console.log("dés 2", faceDice2);
      
      if (faceDice1 + faceDice2 === total) {
        res++
      }
    }
  }
  return res;
}
/*<===================== FUNCTION FOR 2 DICES*/

resultat.value = getTotalPossibleConfigurations(7, numberOfDices.value, numberOfFace.value);

defineExpose({ resultat, numberOfDices, numberOfFace });
</script>

<style scoped>
</style>
