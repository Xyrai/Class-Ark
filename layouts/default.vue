<template>
  <div>
    <header
      class="h-20 px-7 flex border-b border-b-[#ffffff80] fixed top-0 left-0 right-0 text-[#ffffff50] z-10"
    >
      <nav class="h-full w-full flex items-center">
        <a href="" class="aspect-[163/47]">
          <nuxt-img
            src="/logo.png"
            alt="Lost Ark Logo"
            format="webp"
            width="163"
            height="47"
          />
        </a>
        <ul
          class="flex items-center w-full h-full gap-x-12 text-xl -mb-[1px] font-ibm"
        >
          <li
            class="ml-12 drop-shadow h-full flex justify-center items-center w-28"
            :class="
              swiperIndex === 0 ? 'border-b-white border-b text-white' : null
            "
          >
            <button class="tracking-wider" @click="setSwiperIndex(0)">
              OVERVIEW
            </button>
          </li>
          <li
            class="drop-shadow h-full flex justify-center items-center w-28"
            :class="
              swiperIndex === 1 ? 'border-b-white border-b text-white' : null
            "
          >
            <button class="tracking-wider" @click="setSwiperIndex(1)">
              ABILITIES
            </button>
          </li>
          <li
            class="drop-shadow h-full flex justify-center items-center w-28"
            :class="
              swiperIndex === 2 ? 'border-b-white border-b text-white' : null
            "
          >
            <button class="tracking-wider" @click="setSwiperIndex(2)">
              GAMEPLAY
            </button>
          </li>
          <!-- <li class="ml-auto drop-shadow">
            <a class="tracking-wider" href="#">CLASSES</a>
          </li> -->
        </ul>
      </nav>
    </header>
    <slot />
  </div>
</template>

<script setup lang="ts">
const swiperIndex = useState("swiperIndex", () => 0);
const swiper = useState("swiper");

const setSwiperIndex = (index: number) => {
  swiperIndex.value = index;
  swiper?.value.slideTo(index);
};
</script>
