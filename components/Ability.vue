<template>
  <li class="flex flex-col items-center justify-end">
    <button
      class="pb-1 transition-all duration-500"
      :class="active ? '-translate-y-3 border-b  border-[#D0A85C]' : null"
    >
      <img
        src="@/assets/img/artist-ultimate-1.png"
        alt=""
        class="w-full h-full aspect-square"
      />
    </button>
    <div v-if="active" class="h-5 mt-3 w-[1px] bg-[#D0A85C]"></div>
    <Bullet :active="active" :class="active ? '-mb-[10px]' : '-mb-1 mt-5'" />
  </li>
</template>

<script setup lang="ts">
defineProps({
  active: Boolean,
});
</script>
