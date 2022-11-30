<template>
  <ul class="flex gap-5">
    <Ability
      v-for="ability in test"
      :key="ability"
      :active="selectedAbility === ability ? true : false"
      @click="selectAbility(ability)"
    />
  </ul>

  <hr class="w-full border-t-[#ffffff50] h-[1px]" />

  <div class="mt-16 flex flex-col gap-2">
    <span class="text-[#FFFFFF40] text-2xl">ULTIMATE</span>
    <h2 class="text-3xl font-bold">Dreamy Peach Garden</h2>
    <p class="text-2xl">"Levitate in the swirl of flower petals..."</p>
  </div>
</template>

<script setup lang="ts">
defineProps({
  abilities: Array<String>,
});

const test = ["a", "b", "c", "d", "e"];
const selectedAbility = ref(test[0]);

const selectAbility = (ability: string) => {
  selectedAbility.value = ability;
};
</script>

<style scoped></style>
