<script setup>
const model = defineModel({
  default: {
    depense: 300,
    interest: 12.25,
    during: 84,
    solde: 2000,
    salaire: 1200,
  },
});
const $emit = defineEmits("calculate");
</script>
<template>
  <aside class="min-w-48 px-4">
    <div>
      <label>Dépense</label>
      <UInput v-model="model.depense" />
    </div>
    <div>
      <label>Intérêt</label>
      <UInput v-model="model.interest" />
    </div>
    <div>
      <label>Durée</label>
      <UInput v-model="model.during" />
    </div>
    <div>
      <label>Solde</label>
      <UInput v-model="model.solde" />
    </div>
    <div>
      <label>Salaire</label>
      <UInput v-model="model.salaire" />
    </div>
    <UButton class="w-full" label="Calculer" @click="$emit('calculate')" />
  </aside>
</template>
