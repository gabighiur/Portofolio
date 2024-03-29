<script setup>
/* eslint no-undef: "error" */
import img1 from '~/assets/1.png'
import img2 from '~/assets/2.jpg'
import img3 from '~/assets/3.png'
import img4 from '~/assets/4.png'

function goBack() {
  window.history.back()
}
</script>

<template>
  <section class="bgcook min-h-screen flex">
    <div class="flex items-center justify-center">
      <img :src="img1">
    </div>
  </section>
  <section class="bgcook">
    <div class="w-1/2 flex flex-row items-center">
      <img :src="img2">
      <img :src="img3">
    </div>
  </section>
  <section class="bgcook">
    <div class="h-full shadow-sm">
      <img :src="img4">
    </div>
  </section>
  <section class="bgcook sedonaText flex flex-col gap-4 p-20 text-left">
    <h1 class="sedonaText text-4xl text-white">
      COOKHOUSE
    </h1>
    <hr border-1 border-red-400>
    <p class="lookoutText text-cyan-100">
      {{ $t('cookhouse.desc') }}
    </p>
    <div class="flex flex-row items-center gap-8 p-2">
      <button class="cursor-pointer rounded bg-red-400 px-4 py-2 font-bold text-white hover:bg-red-300" @click="goBack">
        {{ $t('button.back') }}
      </button>
    </div>
  </section>
</template>
