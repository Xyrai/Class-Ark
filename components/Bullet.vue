<template>
  <div
    class="w-5 h-5 bg-current flex items-center justify-center z-30 rounded-full relative"
    v-if="active"
  >
    <div
      class="w-4 h-4 bg-black rounded-full z-20 flex items-center justify-center"
    >
      <div class="w-2 h-2 bg-current rounded-full z-10 transition-color"></div>
    </div>
  </div>
  <div v-else>
    <div
      class="w-2 h-2 bg-current rounded-full z-10 transition-all duration-500"
    ></div>
  </div>
</template>

<script setup lang="ts">
defineProps({
  active: Boolean,
});
</script>
