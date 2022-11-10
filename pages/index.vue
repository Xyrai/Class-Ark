<template>
  <main
    class="pt-20 bg-[url('@/assets/img/bg-artist.png')] h-screen bg-cover bg-no-repeat relative"
  >
    <!-- <div>
      <img src="https://picsum.photos/500" alt="" />
    </div> -->
    <swiper
      :slides-per-view="1"
      :modules="modules"
      :loop="true"
      class="w-full h-full text-white"
    >
      <swiper-slide>
        <p>LOL TEST</p>
      </swiper-slide>
    </swiper>
    <img
      src="@/assets/img/artist.png"
      alt=""
      class="absolute bottom-0 right-0"
    />
  </main>
</template>

<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import { Pagination } from "swiper";

import "swiper/css";
import "swiper/css/pagination";

const modules = [Pagination];
</script>
