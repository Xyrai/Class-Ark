<template>
  <main class="h-screen">
    <swiper
      :modules="modules"
      :slides-per-view="1"
      :allow-touch-move="false"
      :navigation="swiperNavOptions"
      class="w-full h-full text-white"
    >
      <swiper-slide
        class="bg-[url('@/assets/img/bg-artist.png')] h-full bg-cover bg-no-repeat relative w-full pt-20"
      >
        <p>LOL TEST</p>
        <nuxt-img
          src="/artist.png"
          alt=""
          class="absolute bottom-0 right-0"
          draggable="false"
        />
      </swiper-slide>
      <swiper-slide
        class="bg-[url('@/assets/img/bg-artist.png')] h-full bg-cover bg-no-repeat relative w-full"
      >
        <p>LOL TEST</p>
        <img
          src="@/assets/img/artist.png"
          alt=""
          class="absolute bottom-0 right-0"
        />
      </swiper-slide>
      <swiper-slide
        class="bg-[url('@/assets/img/bg-artist.png')] h-full bg-cover bg-no-repeat relative w-full"
      >
        <p>LOL TEST</p>
        <img
          src="@/assets/img/artist.png"
          alt=""
          class="absolute bottom-0 right-0"
        />
      </swiper-slide>
    </swiper>

    <button class="swiper-button-prev" @click="updateIndex('prev')">
      prev
    </button>
    <button class="swiper-button-next" @click="updateIndex('next')">
      next
    </button>
  </main>
</template>

<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import { Navigation, Pagination } from "swiper";
import { NavigationOptions } from "swiper/types";
import "swiper/css";
import "swiper/css/pagination";

const swiperNavOptions: NavigationOptions = {
  prevEl: ".swiper-button-prev",
  nextEl: ".swiper-button-next",
};

// const testSwiper = useSwiper();
const modules = [Pagination, Navigation];
const swiperState = useState("swiperIndex", () => 0);

const updateIndex = (value: string) => {
  if (value === "prev" && swiperState.value > 0) {
    swiperState.value--;
    return;
  }

  swiperState.value++;
};
</script>
