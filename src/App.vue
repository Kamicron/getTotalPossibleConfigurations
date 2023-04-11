<template>
  <div>
    <p>Il y a {{ resultat }} facon de faire {{ total }} avec {{ numberOfDices }} dés de {{ numberOfFace }} faces
</p>
    <p>Temps d'execution {{ executionTime }} ms</p>
  </div>
</template>
  
<script setup lang="ts">
import { ref } from 'vue';

const numberOfDices = ref<number>(12);
const numberOfFace = ref<number>(6);
const total = ref<number>(28);
const resultat = ref<number>(0);
const executionTime = ref<number>(0);
/*>===================== V1: FUNCTION FOR 2 DICES*/
// function getTotalPossibleConfigurations(total: number, numberOfDices: number, numberOfFace: number): number {
//   let res = 0;

//   console.log("t", total, "nb", numberOfDices, "faces", numberOfFace);
//   for (let faceDice1 = 1; faceDice1 <numberOfFace+1; faceDice1++) {
//     for (let faceDice2 = 1; faceDice2 <numberOfFace+1; faceDice2++) {
//       console.log("dés 1", faceDice1);
//       console.log("dés 2", faceDice2);
      
//       if (faceDice1 + faceDice2 === total) {
//         res++
//       }
//     }
//   }
//   return res;
// }
/*<===================== FUNCTION FOR 2 DICES*/

/*>===================== V2: FUNCTION FOR x DICES*/
function getTotalPossibleConfigurations(total: number, numberOfDices: number, numberOfFace: number): number {
  let res = 0;
  if (numberOfDices === 0) {
    return total === 0 ? 1 : 0;
  }
  for (let faceDice = 1; faceDice <numberOfFace+1; faceDice++) {
      res += getTotalPossibleConfigurations(total - faceDice, numberOfDices-1, numberOfFace)
  }
  return res;
}
/*<===================== FUNCTION FOR 2 DICES*/
console.log("====== START =====");

const startTime = performance.now();
resultat.value = getTotalPossibleConfigurations(total.value, numberOfDices.value, numberOfFace.value);
const endTime = performance.now();
executionTime.value = endTime - startTime;

console.log("====== FIN =====");

</script>

<style scoped>
</style>
