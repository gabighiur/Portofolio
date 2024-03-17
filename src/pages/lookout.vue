<script setup>
import look from '~/lookout/look.jpg'
import bridge from '~/lookout/pngs/bridge.png'
import bridgeUp from '~/lookout/pngs/bridgeUp.png'
import moon from '~/lookout/pngs/moon.png'
import look2 from '~/lookout/look2.jpg'
import prch from '~/lookout/pngs/prch.png'
import trees from '~/lookout/pngs/trees.png'
import birds from '~/lookout/pngs/birds.png'

const colorPalette = [
  { name: 'RoseWood', code: '#CA7F63' },
  { name: 'Velvet', code: '#F38B82' },
  { name: 'Copper', code: '#AF4C51' },
]

function copyToClipboard(code, notificationId) {
  navigator.clipboard.writeText(code)
  const notification = document.getElementById(notificationId)
  notification.style.opacity = '1'
  setTimeout(() => {
    notification.style.opacity = '0'
  }, 3000)
}
function goBack() {
  window.history.back()
}
</script>

<template>
  <!-- First Section -->
  <section class="bglook relative min-h-screen flex flex-col items-center justify-center p-10 lg:justify-start md:justify-stretch">
    <div class="flex flex-col items-center p-8 lg:flex-row md:flex-row sm:flex-col">
      <img :src="moon" alt="The Moon Image" class="relative top-0 w-20 lg:w-40 md:w-20">
      <div class="lookoutText flex-1 items-center">
        <header>
          <div class="mb-0 text-left sm:mb-20">
            <h1 class="text-6xl text-cyan-950 lg:text-7xl md:text-7xl sm:text-7xl">
              {{ $t('look.title') }}
            </h1>
            <p class="ml-2 text-xl text-cyan-950 md:text-2xl">
              {{ $t('look.tag') }}
            </p>
          </div>
        </header>
      </div>
      <div class="flex-1 p-4">
        <img :src="look" alt="The Lookout Poster">
      </div>
    </div>
    <img :src="bridge" alt="The Bridge Image" class="absolute bottom-0">
  </section>

  <!-- Second Section -->
  <section class="bglook relative min-h-screen flex items-start items-center justify-center p-10">
    <div class="flex flex-col items-center p-8 lg:flex-row md:flex-col sm:flex-col">
      <div class="border-gold md:w-l lg:w-l z-1 mr-0 flex-1 border-2 p-2 lg:mr-20 sm:w-xl">
        <div class="border-gold">
          <img :src="look2" alt="Left Image">
        </div>
      </div>

      <div class="lookoutText flex-1 items-center">
        <div class="mt-10 text-left sm:mt-20">
          <h2 class="text-4xl text-cyan-950 lg:text-7xl md:text-6xl sm:text-5xl">
            {{ $t('look.overview') }}
          </h2>
          <p class="ml-0 mt-2 text-sm text-cyan-950 lg:mt-6 md:mt-4 lg:text-2xl md:text-2xl sm:text-2xl">
            {{ $t('look.about1') }}
          </p>
          <p class="ml-0 mt-2 text-sm text-cyan-950 lg:mt-6 md:mt-4 lg:text-2xl md:text-2xl sm:text-2xl">
            {{ $t('look.about2') }}
          </p>
        </div>

        <div class="z-50 mt-8 lg:mt-16 md:mt-12" />
      </div>
    </div>
    <img :src="bridgeUp" alt="The Bridge Image" class="absolute top-0 z-0 opacity-15 blur-lg">
    <img :src="prch" alt="Additional Image" class="z-40 w-20 md:w-25">
    <img :src="trees" alt="The Bridge Image" class="absolute bottom-0 z-30">
  </section>

  <!-- Third Section -->
  <section class="bglook relative flex items-start justify-center p-2">
    <!-- <img :src="trees" alt="The Trees Image" class="absolute top-0 w-full rotate-x-180 transform opacity-20"> -->
    <div class="flex flex-col items-center p-8 lg:flex-row md:flex-row sm:flex-col">
      <div class="lookoutText w-full lg:w-1/2 md:w-1/2 sm:w-full">
        <div class="mt-10 text-left">
          <h2 class="text-4xl text-cyan-950 lg:text-7xl md:text-6xl sm:text-5xl">
            {{ $t('look.pallete') }}
          </h2>
          <p class="ml-0 mt-2 text-sm text-cyan-950 lg:mt-6 md:mt-4 lg:text-2xl md:text-2xl sm:text-2xl">
            {{ $t('look.aboutPallete') }}
          </p>
        </div>
        <div class="mt-4 flex flex-wrap items-center justify-center gap-4 rounded-xl bg-cyan-950 p-4">
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
      <div class="mt-4 flex flex-col items-center justify-center lg:w-1/2 md:w-1/2 sm:w-full sm:flex-row">
        <img :src="birds" alt="Birds Image" class="w-1/2">
      </div>
    </div>
  </section>
  <section class="bglook p-10">
    <div class="flex flex-row items-center gap-8">
      <button class="cursor-pointer rounded px-4 py-2 font-bold text-white hover:bg-orange-300" :style="{ backgroundColor: colorPalette.find(color => color.name === 'Copper').code } " @click="goBack">
        Go Back
      </button>
    </div>
  </section>
</template>
