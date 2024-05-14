<script>
/* eslint no-undef: "error" */
import image from '~/assets/mock.png'

export default {
  data() {
    return {
      image,
    }
  },
  methods: {
    goBack() {
      window.history.back()
    },
  },
}
</script>

<template>
  <section class="relative min-h-screen flex flex-col items-center justify-center bg-teal-950 p-10">
    <div class="flex flex-col items-center gap-8 p-2 lg:flex-row md:flex-row sm:flex-col">
      <div class="flex-1 p-2">
        <img :src="image" alt="Website Image">
      </div>
      <div class="flex-1 items-center">
        <header>
          <div class="mb-0 flex flex-col gap-4 text-left sm:mb-20">
            <h1 class="text-4xl font-bold text-white lg:text-7xl md:text-7xl">
              GOLDMAN
            </h1>
            <p class="text-l ml-2 text-white md:text-2xl">
              {{ $t('barber.desc') }}
            </p>
            <div class="flex flex-row justify-center gap-4 bg-amber-200 p-2 opacity-50">
              <div i="skill-icons-vuejs-light" icon-btn class="text-2xl" />
              <div i="skill-icons-tailwindcss-light" class="text-2xl" />
            </div>
            <div class="flex flex-row items-center gap-8">
              <a
                href="https://goldman.vercel.app/"
                target="_blank"
                rel="noreferrer"
                title="Hyena Website"
                class="group relative flex items-center text-white hover:text-amber-200"
              >
                <div i-bi-globe class="text-l mr-2" />
                <div class="relative text-xl">Visit Website</div>
                <span class="absolute inset-x-0 bottom--1 h-[2px] scale-x-0 transform bg-amber-200 transition-transform duration-300 ease-in-out group-hover:scale-x-100" />
              </a>
              <a
                href="https://github.com/OvoOno-Studio/vue-dapp"
                target="_blank"
                rel="noreferrer"
                title="Hyena Website"
                class="group relative flex items-center text-white hover:text-amber-200"
              >
                <div i-carbon-logo-github class="mr-2 text-xl" />
                <div class="relative text-xl">GitHub</div>
                <span class="absolute inset-x-0 bottom--1 h-[2px] scale-x-0 transform bg-amber-200 transition-transform duration-300 ease-in-out group-hover:scale-x-100" />
              </a>
            </div>
            <div class="flex flex-row items-center gap-8">
              <button btn class="bg-amber-200 px-4 py-2 font-bold text-cyan-950 hover:bg-amber-100" @click="goBack">
                {{ $t('button.back') }}
              </button>
            </div>
          </div>
        </header>
      </div>
    </div>
  </section>
</template>
