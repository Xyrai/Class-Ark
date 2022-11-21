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
          class="flex items-center w-full gap-x-12 text-xl shadow font-[IBM_Plex_Sans]"
        >
          <li class="ml-12">
            <a href="#" :class="swiperIndex === 0 ? 'text-white' : null"
              >OVERVIEW</a
            >
          </li>
          <li>
            <a href="#" :class="swiperIndex === 1 ? 'text-white' : null"
              >ABILITIES</a
            >
          </li>
          <li>
            <a href="#" :class="swiperIndex === 2 ? 'text-white' : null"
              >GAMEPLAY</a
            >
          </li>
          <li class="ml-auto"><a href="#">CLASSES</a></li>
        </ul>
      </nav>
    </header>
    <slot />
  </div>
</template>

<script setup lang="ts">
const swiperIndex = useState("swiperIndex");
</script>
