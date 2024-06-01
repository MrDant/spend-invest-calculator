<script setup>
import { useLocalStorage } from "@vueuse/core";
const params = useLocalStorage("params", {
  depense: 105.98,
  interest: 11,
  during: 84,
  solde: 7500,
  salaire: 0,
});

const data = ref([]);
function update() {
  const newData = [];
  const interest = params.value.interest / 100 / 12;
  let solde = +params.value.solde;
  for (let i = 0; i < params.value.during; i++) {
    newData.push({
      x: (i % 12) + 1 + "/" + (2024 + Math.floor(i / 12)),
      y: Math.round(solde * 100) / 100,
    });
    solde += +solde * +interest;
    solde -= +params.value.depense;
    solde += +params.value.salaire;
  }
  data.value = newData;
}
update();
</script>

<template>
  <div>
    <Header />
    <UDivider />
    <div class="flex w-full">
      <Aside v-model="params" @calculate="update" />
      <Graph class="flex-1" :data="[data]" />
    </div>
  </div>
</template>
