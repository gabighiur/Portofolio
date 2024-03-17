<script setup>
import look from '~/lookout/look.jpg'
import bridge from '~/lookout/pngs/bridge.png'
import bridgeUp from '~/lookout/pngs/bridgeUp.png'
import moon from '~/lookout/pngs/moon.png'
import look2 from '~/lookout/look2.jpg'
import prch from '~/lookout/pngs/prch.png'
import trees from '~/lookout/pngs/trees.png'
import birds from '~/lookout/pngs/birds.png'
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
  <section class="bglook relative min-h-screen flex items-start items-center justify-center p-2">
    <img :src="bridgeUp" alt="The Bridge Image" class="absolute top-0">
    <div class="flex flex-col items-center p-8 lg:flex-row md:flex-col sm:flex-col">
      <div class="border-gold md:w-l lg:w-l mr-0 flex-1 border-2 p-2 lg:mr-20 sm:w-xl">
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

        <div class="mt-8 lg:mt-16 md:mt-12">
          <img :src="prch" alt="Additional Image" class="w-20 md:w-25">
        </div>
      </div>
    </div>
    <img :src="trees" alt="The Bridge Image" class="absolute bottom-0">
  </section>

  <!-- Third Section -->
  <section class="bglook relative flex items-start justify-center p-2">
    <img :src="trees" alt="The Trees Image" class="absolute top-0 w-full rotate-x-180 transform opacity-20">
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
        <div class="mt-4 flex items-center justify-center gap-4 bg-cyan-950 p-4">
          <div class="rosewood h-10 w-1/3">
            <p class="text-sm text-cyan-50">
              #F38B82
            </p>
          </div>
          <div class="copper h-10 w-1/3">
            <p class="text-sm text-cyan-50">
              AF4C51
            </p>
          </div>
          <div class="bglook h-10 w-1/3">
            <p class="text-sm text-cyan-50">
              #CA7F63
            </p>
          </div>
        </div>
      </div>
      <div class="mt-4 flex items-center justify-center lg:w-1/2 md:w-1/2 sm:w-full">
        <img :src="birds" alt="Birds Image" class="w-1/2">
      </div>
    </div>
  </section>
</template>
