<script>
/* eslint no-undef: "error" */
import bgremover from '~/assets/bgr/remover.png'
import hyena from '~/assets/hyenapreview.png'
import barber from '~/assets/projectsimg/mock2.png'
import lookout from '~/assets/projectsimg/lookout.jpg'
import cook from '~/assets/cookhouse/preview.png'

export default {
  name: 'TheSection2',
  data() {
    return {
      projects: [
        { id: 1, image: hyena, routeName: 'hyena' },
        { id: 2, image: barber, routeName: 'barber' },
        { id: 3, image: bgremover, routeName: 'bgremover' },
        { id: 4, image: lookout, routeName: 'lookout' },
        { id: 5, image: cook, routeName: 'logos' },
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
          <img
            :src="project.image"
            alt="Project Image"
            class="mx-auto mb-4 h-50 object-cover"
          >
          <button>
            <p class="mt-4 bg-emerald-100 px-3 py-1 text-xs text-cyan-950">
              {{ $t('work.button') }}
            </p>
          </button>
        </router-link>
      </div>
    </div>
  </section>
</template>
