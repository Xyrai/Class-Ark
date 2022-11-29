<template>
  <li
    class="flex flex-col items-center justify-end hover:text-[#D0A85C]"
    :class="active ? 'text-[#D0A85C]' : 'hover:text-[#D0A85C] cursor-pointer'"
  >
    <button
      class="pb-1 transition-transform duration-500"
      :class="active ? '-translate-y-3' : 'hover:-translate-y-2'"
    >
      <img
        src="@/assets/img/artist-ultimate-1.png"
        alt=""
        class="w-full h-full aspect-square"
        draggable="false"
      />
    </button>
    <div
      class="h-5 w-[1px] bg-[#D0A85C] transition-all duration-500"
      :class="active ? 'scale-y-100 opacity-100' : 'scale-y-0 opacity-0'"
    ></div>
    <Bullet :active="active" :class="active ? '-mb-[10px]' : '-mb-1'" />
  </li>
</template>

<script setup lang="ts">
defineProps({
  active: Boolean,
});
</script>
