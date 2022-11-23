<template>
  <main class="h-screen">
    <swiper
      @swiper="onSwiper"
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
      <img
        src="@/assets/img/arrow-left.svg"
        class="swiper-button-prev absolute left-0 top-0 bottom-0 z-10 my-auto"
        :class="swiperState > 0 ? 'cursor-pointer' : 'hidden'"
        @click="updateIndex('prev')"
      />
      <img
        src="@/assets/img/arrow-right.svg"
        class="swiper-button-next absolute right-0 top-0 bottom-0 z-10 my-auto"
        :class="
          swiperState >= 0 && swiperState < 2 ? 'cursor-pointer' : 'hidden'
        "
        @click="updateIndex('next')"
      />
    </swiper>
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

const modules = [Pagination, Navigation];
const swiperState = useState("swiperIndex");
const swiperRef = ref(null);

const onSwiper = (swiper: typeof Swiper) => {
  swiperRef.value = swiper;
  useState("swiper", () => swiper);
};

const updateIndex = (value: string) => {
  if (value === "prev" && swiperState.value > 0) {
    swiperState.value--;
    return;
  }

  if (value === "next" && swiperState.value >= 0 && swiperState.value < 2) {
    swiperState.value++;
    return;
  }
};
</script>
