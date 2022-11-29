<template>
  <ul class="flex gap-4">
    <Ability
      v-for="ability in test"
      :key="ability"
      :active="selectedAbility === ability ? true : false"
      @click="selectAbility(ability)"
    />
  </ul>
</template>

<script setup lang="ts">
defineProps({
  abilities: Array<String>,
});

const test = ["a", "b", "c", "d"];
const selectedAbility = ref(test[0]);

const selectAbility = (ability: string) => {
  selectedAbility.value = ability;
};
</script>

<style scoped></style>
