<script>
/* eslint no-undef: "error" */
import hyenaImg from '~/assets/hyenapreview.png'
import barberImg from '~/assets/mock2.png'
import cookImg from '~/assets/preview.png'
import owlImg from '~/assets/owlpreview.png'

export default {
  name: 'Portofolio',
  data() {
    return {
      projects: [
        { id: 1, image: owlImg, routeName: 'owl', label: 'Night Owls Web App' },
        { id: 2, image: barberImg, routeName: 'barber', label: 'GoldMan Barbershop Web App' },
        { id: 3, image: hyenaImg, routeName: 'hyena', label: 'Hyenas Web App' },
        { id: 4, image: cookImg, routeName: 'logos', label: 'Logofolio' },
      ],
    }
  },
}
</script>

<template>
  <section id="section02" class="min-h-screen flex items-center justify-center bg-cyan-950 p-8">
    <div class="w-full max-w-screen-xl border-2 border-emerald-100 p-8 text-center">
      <h1 class="mb-8 text-3xl font-bold text-emerald-100">
        {{ $t('work.title') }}
      </h1>
      <div class="grid grid-cols-1 gap-4 sm:grid-cols-3">
        <router-link
          v-for="project in projects"
          :key="project.id"
          :to="{ name: project.routeName }"
          class="mb-4 border-2 border-emerald-100 p-4"
        >
          <h2 m-8 text-2xl tracking-wide text-emerald-100>
            {{ project.label }}
          </h2>
          <img
            :src="project.image"
            alt="Project Image"
            class="mx-auto mb-4 h-50 object-cover"
          >
          <button btn>
            <p class="px-3 py-1 text-xs text-cyan-950">
              {{ $t('work.button') }}
            </p>
          </button>
        </router-link>
      </div>
    </div>
  </section>
</template>
