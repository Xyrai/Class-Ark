<template>
  <div
    class="w-5 h-5 bg-[#D0A85C] flex items-center justify-center z-30 rounded-full relative"
    v-if="active"
  >
    <div
      class="w-4 h-4 bg-black rounded-full z-20 flex items-center justify-center"
    >
      <div class="w-2 h-2 bg-[#D0A85C] rounded-full z-10"></div>
    </div>
  </div>
  <div v-else>
    <div class="w-2 h-2 bg-[#D9D9D9] rounded-full z-10"></div>
  </div>
</template>

<script setup lang="ts">
defineProps({
  active: Boolean,
});
</script>
