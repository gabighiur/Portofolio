<script>
export default {
  name: 'TheSection1',

}
</script>

<template>
  <section id="section01" class="min-h-screen flex items-center justify-center bg-emerald-100 p-8">
    <div class="p-20 text-left">
      <h1 class="ml--2 text-6xl font-bold leading-tight text-cyan-950 xl:text-9xl">
        {{ $t('header.title') }}
      </h1>
      <p class="text-xl text-cyan-950 xl:w-1/2">
        {{ $t('header.desc') }}
      </p>
      <div class="mt-4">
        <router-link to="portofolio" class="text-s cursor-pointer text-cyan-950 underline underline-offset-1 lg:text-xl md:text-xl sm:text-xs">
          {{ $t('header.inspect') }}
        </router-link>
      </div>
    </div>
  </section>
</template>
