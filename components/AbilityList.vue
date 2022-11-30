<template>
  <ul class="flex gap-5">
    <Ability
      v-for="ability in abilities"
      :key="ability.name"
      @click="selectAbility(ability)"
      :ability="ability"
      :active="selectedAbilityName === ability.name ? true : false"
    />
  </ul>

  <hr class="w-full border-t-[#ffffff50] h-[1px]" />

  <div class="mt-16 flex flex-col gap-2">
    <span class="text-[#FFFFFF40] text-2xl font-ibmserif uppercase">{{
      selectedAbility.category
    }}</span>
    <h2 class="text-3xl font-semibold font-ibmserif">
      {{ selectedAbility.name }}
    </h2>
    <p class="text-2xl font-ibm">"{{ selectedAbility.description }}"</p>
  </div>
</template>

<script setup lang="ts">
import { IAbility } from "@/interfaces/IAbility";

const props = defineProps({
  abilities: Array<IAbility>,
});

const selectedAbility = ref(props.abilities[0]);
const selectedAbilityName = ref(props.abilities[0].name);

const selectAbility = (ability: IAbility) => {
  selectedAbility.value = ability;
  selectedAbilityName.value = ability.name;
  useState("ability").value = ability;
};
</script>

<style scoped></style>
