<script setup>
import underH from '~/assets/hdr.png'
import header from '~/assets/poster1.jpg'
import over from '~/assets/over.jpg'
import hugePoster from '~/assets/poster2.jpg'

const colorPalette = [
  { name: 'Light Sage Green', code: '#A8D5B1' },
  { name: 'Olive Green', code: '#B1A64A' },
  { name: 'Grayish Olive Green', code: '#72976B' },

]

function copyToClipboard(code, notificationId) {
  navigator.clipboard.writeText(code)
  const notification = document.getElementById(notificationId)
  notification.style.opacity = '1'
  setTimeout(() => {
    notification.style.opacity = '0'
  }, 3000)
}
</script>

<template>
  <!-- Header Section -->
  <section class="bgsedona relative min-h-screen flex items-center justify-center p-4 lg:items-start">
    <div class="flex flex-col items-center gap-4 lg:flex-row md:flex-row sm:flex-col lg:gap-40">
      <header class="sedonaText">
        <h1 class="flex cursor-pointer items-start text-6xl tracking-tight text-white transition-all duration-300 ease-out lg:text-9xl md:text-7xl sm:text-7xl hover:tracking-wide">
          {{ $t('sedona.title') }}
        </h1>
      </header>
      <img :src="header" alt="The Sedona Poster" class="w-2/5 flex items-center justify-center p-4 lg:w-sm">
    </div>

    <img :src="underH" alt="The Bridge Image" class="absolute bottom-0 h-auto">
  </section>

  <section>
    <div class="h-auto">
      <img :src="hugePoster" alt="Sedona Huge Poster">
    </div>
  </section>

  <!-- Second Section -->
  <section class="bgsedona relative min-h-screen flex items-center justify-around p-2">
    <div class="flex flex-col gap-8 p-8 lg:flex-row md:flex-col sm:flex-col">
      <div class="sedonaText flex-1 items-center">
        <div class="line-clamp-2 text-left hover:line-clamp-none">
          <h2 class="text-4xl text-white lg:text-6xl md:text-6xl sm:text-5xl">
            {{ $t('sedona.overview') }}
          </h2>
          <p class="mt-2 text-wrap text-sm text-white lg:mt-6 md:mt-4 lg:text-2xl md:text-2xl sm:text-2xl">
            {{ $t('sedona.about1') }}
          </p>
          <p class="mt-2 text-sm text-white lg:mt-6 md:mt-4 lg:text-2xl md:text-2xl sm:text-2xl">
            {{ $t('sedona.about2') }}
          </p>
        </div>
      </div>
      <div class="border-gold md:w-l lg:w-l mr-0 flex-1 border-2 p-2 lg:mr-20 sm:w-xl">
        <div class="border-gold">
          <img :src="over" alt="Left Image">
        </div>
      </div>
    </div>
  </section>

  <!-- Third Section -->
  <section class="bgsedona relative min-h-screen flex items-center justify-center p-2">
    <div class="flex flex-col items-center gap-8 p-8 lg:flex-row">
      <div class="sedonaText text-center lg:w-1/2 md:w-1/2 sm:w-full lg:text-left">
        <div class="text-left">
          <h2 class="mb-4 text-4xl text-white lg:text-6xl md:text-6xl sm:text-5xl">
            {{ $t('sedona.pallete') }}
          </h2>
          <p class="text-white lg:text-2xl md:text-2xl sm:text-2xl">
            {{ $t('sedona.aboutPallete') }}
          </p>
        </div>
      </div>
      <div class="mt-4 flex flex-wrap items-center justify-center gap-4 rounded-xl bg-lime-950 p-4">
        <div v-for="(color, index) in colorPalette" :key="index" class="flex flex-col items-center">
          <p class="text-white">
            {{ color.name }}
          </p>
          <div :style="{ backgroundColor: color.code }" class="h-20 w-20 flex items-center justify-center rounded-full">
            <p class="text-sm text-cyan-50">
              {{ color.code }}
            </p>
          </div>
          <div class="relative mt-2">
            <div i="mdi-content-copy" class="text-white hover:text-green-300" @click="copyToClipboard(color.code, `copyNotification${index}`)" />
            <div
              :id="`copyNotification${index}`"
              class="group absolute left-0 top-0 mt-10 border border-neutral-200/60 rounded-md bg-white px-3 py-1 text-xs text-neutral-500 opacity-0 transition-opacity duration-300 ease-in-out active:bg-white focus:bg-white hover:bg-neutral-100 hover:text-neutral-600 focus:outline-none"
            >
              Copied to Clipboard
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
