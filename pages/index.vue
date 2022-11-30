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
        <div class="ml-28 flex flex-col gap-x-2 items-center w-[634px] mt-60">
          <div>
            <img
              class="aspect-[127/116] z-10"
              src="@/assets/img/icon-artist.svg"
              alt=""
            />
          </div>
          <h1
            class="first-letter:text-[100px] text-[85px] font-ibmserif tracking-wider z-10"
          >
            ARTIST
          </h1>
          <p class="text-3xl mt-10 z-10 font-light">
            "I'm going to draw, to protect you and everyone..."
          </p>
        </div>
        <nuxt-img
          src="/artist.png"
          alt=""
          class="absolute bottom-0 right-0"
          draggable="false"
        />
      </swiper-slide>
      <swiper-slide
        class="bg-[url('@/assets/img/bg-abilities.png')] h-full bg-cover bg-no-repeat relative w-full pt-20"
      >
        <div class="flex w-full h-full justify-between px-60">
          <div class="flex flex-col mt-56 w-full">
            <h1
              class="first-letter:text-[100px] text-[85px] font-ibmserif tracking-wider z-10 leading-none"
            >
              ABILITIES
            </h1>

            <div class="flex flex-col mt-44">
              <AbilityList :abilities="abilities" />
            </div>
          </div>

          <div class="mt-60">
            <video
              id="abilityVideo"
              :src="`/${currentAbility.videoUrl}`"
              class="aspect-[737/420] right-60 w-full border-2 border-[#ffffff50] p-1"
              :autoplay="swiperState == 1 ? true : null"
              :playsinline="swiperState == 1 ? true : null"
              controls
              loop
            ></video>
          </div>
        </div>
      </swiper-slide>
      <swiper-slide
        class="bg-[url('@/assets/img/bg-artist-video.png')] flex justify-center items-center z-10 h-full bg-cover bg-no-repeat relative w-full pt-20"
      >
        <div class="absolute inset-0 bg-black opacity-70 -z-10"></div>

        <div class="border-2 w-3/4">
          <iframe
            src="https://www.youtube.com/embed/wl0q0xi10Ng?controls=1"
            title="YouTube video player"
            frameborder="0"
            class="aspect-[1460/821] w-full h-full"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen
            autoplay
          ></iframe>
        </div>
      </swiper-slide>
      <img
        src="@/assets/img/arrow-left.svg"
        class="swiper-button-prev absolute left-7 top-0 bottom-0 z-10 my-auto transition-opacity hover:opacity-60"
        :class="swiperState > 0 ? 'cursor-pointer' : 'hidden'"
        @click="updateIndex('prev')"
        draggable="false"
      />
      <img
        src="@/assets/img/arrow-right.svg"
        class="swiper-button-next absolute right-7 top-0 bottom-0 z-10 my-auto transition-opacity hover:opacity-60"
        :class="
          swiperState >= 0 && swiperState < 2 ? 'cursor-pointer' : 'hidden'
        "
        @click="updateIndex('next')"
        draggable="false"
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
import { IAbility } from "~~/interfaces/IAbility";
import { emitKeypressEvents } from "readline";

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
  const abilityVideo = document.querySelector("#abilityVideo");

  if (value === "prev" && swiperState.value > 0) {
    // Check if current slide is abilities, then play video else pause
    if (swiperState.value === 2) {
      abilityVideo.play();
    } else {
      abilityVideo.pause();
    }

    swiperState.value--;
    return;
  }

  if (value === "next" && swiperState.value >= 0 && swiperState.value < 2) {
    if (swiperState.value === 0) {
      abilityVideo.play();
    } else {
      abilityVideo.pause();
    }

    swiperState.value++;
    return;
  }
};

const abilities: Array<IAbility> = [
  {
    name: "Dreamy Peach Garden",
    category: "awakening",
    description: "Levitate in the swirl of flower petals...",
    image: "artist-ultimate-1.png",
    videoUrl: "peach.mp4",
  },
  {
    name: "Spectacle",
    category: "awakening",
    description: "Feel the strength of an Artist's scroll...",
    image: "spectacle.webp",
    videoUrl: "spectacle.mp4",
  },
  {
    name: "Hopper",
    category: "ABILITY",
    description: "Ride the brush and bounce up...",
    image: "hopper.webp",
    videoUrl: "hopper.mp4",
  },
  {
    name: "Mirinae",
    category: "ABILITY",
    description:
      "Concentrate dimensional power into the brush to change the space...",
    image: "mirinae.webp",
    videoUrl: "mirinae.mp4",
  },
  {
    name: "Sprinkle",
    category: "ABILITY",
    description: "Concentrate dimensional energy into the brush...",
    image: "sprinkle.webp",
    videoUrl: "sprinkle.mp4",
  },
];

const currentAbility = useState("ability", () => abilities[0]);
</script>
