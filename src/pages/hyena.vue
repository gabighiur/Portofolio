<script>
/* eslint no-undef: "error" */
import image from '~/assets/hyena.png'

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
  <section class="relative min-h-screen flex flex-col items-center justify-center bg-zinc-900 p-10 lg:justify-start md:justify-stretch">
    <div class="flex flex-col items-center gap-8 p-2 lg:flex-row md:flex-row sm:flex-col">
      <div class="flex-1 p-2">
        <img :src="image" alt="Website Image">
      </div>
      <div class="flex-1 items-center">
        <header>
          <div class="mb-0 flex flex-col gap-4 text-left sm:mb-20">
            <h1 class="text-4xl font-sans text-white lg:text-7xl md:text-7xl">
              {{ $t('hyena.title') }}
            </h1>
            <p class="text-l ml-2 text-white md:text-2xl">
              {{ $t('hyena.desc') }}
            </p>
            <div class="flex flex-row justify-center gap-4 bg-red-600 p-2 opacity-50">
              <div i="skill-icons-vuejs-light" class="text-2xl" />
              <div i="skill-icons-tailwindcss-light" class="text-2xl" />
            </div>
            <div class="flex flex-row items-center gap-8">
              <a
                href="https://haha-hyenas.vercel.app/"
                target="_blank"
                rel="noreferrer"
                title="Hyena Website"
                class="group relative flex items-center text-white hover:text-red-600"
              >
                <div i-bi-globe class="text-l mr-2" />
                <div class="relative text-xl">View Live</div>
                <span class="absolute inset-x-0 bottom--1 h-[2px] scale-x-0 transform bg-red-600 transition-transform duration-300 ease-in-out group-hover:scale-x-100" />
              </a>
              <a
                href="https://github.com/OvoOno-Studio/vue-dapp"
                target="_blank"
                rel="noreferrer"
                title="Hyena Website"
                class="group relative flex items-center text-white hover:text-red-600"
              >
                <div i-carbon-logo-github class="mr-2 text-xl" />
                <div class="relative text-xl">GitHub</div>
                <span class="absolute inset-x-0 bottom--1 h-[2px] scale-x-0 transform bg-red-600 transition-transform duration-300 ease-in-out group-hover:scale-x-100" />
              </a>
            </div>
            <div class="flex flex-row items-center gap-8">
              <button class="cursor-pointer rounded bg-red-500 px-4 py-2 font-bold text-white hover:bg-red-700" @click="goBack">
                {{ $t('button.back') }}
              </button>
            </div>
          </div>
        </header>
      </div>
    </div>
  </section>
</template>
