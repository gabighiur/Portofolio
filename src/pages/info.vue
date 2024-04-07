<script setup>
/* eslint no-undef: "error" */
</script>

<template>
  <section id="section01" class="min-h-screen flex items-center justify-center bg-emerald-100 p-8 md:p-20">
    <div class="text-left">
      <h1 class="ml--2 text-5xl font-bold leading-tight text-cyan-950 md:text-6xl">
        {{ $t('about.title') }}
      </h1>
      <hr class="my-6 border-cyan-950 sm:mx-auto">
      <p class="text-xl text-cyan-950 lg:w-1/2 md:text-xl">
        {{ $t('about.desc') }}
      </p>
    </div>
  </section>
  <section id="services" class="min-h-screen flex items-center justify-center bg-emerald-100 p-8">
    <div class="mx-auto container">
      <div class="text-left">
        <h1 class="text-5xl font-bold leading-tight text-cyan-950 md:text-6xl">
          {{ $t('services.title') }}
        </h1>
        <hr class="my-6 border-cyan-950 sm:mx-auto">
      </div>
      <div class="mt-8 flex flex-wrap justify-center">
        <div class="mb-8 w-full px-4 md:w-1/3">
          <div class="text-center">
            <h2 class="text-left text-3xl font-semibold text-cyan-950">
              {{ $t('services.design.title') }}
            </h2>
            <div i-logos:adobe-illustrator />
            <p class="text-left text-lg text-cyan-950">
              {{ $t('services.design.desc') }}
            </p>
          </div>
          <hr class="my-6 border-cyan-950 sm:mx-auto">
        </div>
        <div class="mb-8 w-full px-4 md:w-1/3">
          <div class="text-center">
            <h2 class="text-left text-3xl font-semibold text-cyan-950">
              {{ $t('services.presentation.title') }}
            </h2>
            <div i-logos:adobe-photoshop />
            <p class="text-left text-lg text-cyan-950">
              {{ $t('services.presentation.desc') }}
            </p>
          </div>
          <hr class="my-6 border-cyan-950 sm:mx-auto">
        </div>
        <div class="mb-8 w-full px-4 md:w-1/3">
          <div class="text-center">
            <h2 class="text-left text-3xl font-semibold text-cyan-950">
              {{ $t('services.development.title') }}
            </h2>
            <div i-devicon:vuejs />
            <p class="text-left text-lg text-cyan-950">
              {{ $t('services.development.desc') }}
            </p>
          </div>
          <hr class="my-6 border-cyan-950 sm:mx-auto">
        </div>
      </div>
      <div flex flex-col items-start justify-start px-4>
        <p class="text-left text-lg text-cyan-950">
          {{ $t('plus.text') }}
        </p>
        <div flex flex-row gap-4 text-xl>
          <div i-logos:adobe-premiere />
          <div i-logos:adobe-after-effects />
          <div i-logos:blender />
        </div>
      </div>
    </div>
  </section>
</template>
