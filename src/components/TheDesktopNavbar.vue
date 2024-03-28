<script setup lang="ts">
import { useI18n } from 'vue-i18n'
import { availableLocales, loadLanguageAsync } from '~/modules/i18n'

const { locale } = useI18n()

const HOME = { label: 'nav.item1', route: '/', section: '', icon: '' }
const WORK = { label: 'nav.item2', route: '/portofolio', section: '', icon: '' }
const ABOUT = { label: 'nav.item3', route: '/info', section: '', icon: '' }
const CV = { label: 'nav.item4', route: '/cv', section: '', icon: 'i-pepicons-pencil:cv-circle' }

const NAV_ITEMS = [HOME, WORK, ABOUT]

async function toggleLocales() {
  const locales = availableLocales
  const newLocale = locales[(locales.indexOf(locale.value) + 1) % locales.length]
  await loadLanguageAsync(newLocale)
  locale.value = newLocale
}
</script>

<template>
  <nav sticky top-0 z-50 flex items-center justify-center bg-cyan-950 p-4 px-20>
    <!-- Items Section -->
    <div flex flex-row cursor-pointer items-center text-4xl>
      <router-link
        v-for="item in NAV_ITEMS"
        :key="item.label"
        :to="item.route"
        class="px-4 py-2 text-amber100 hover:text-cyan-200"
        :class="{ 'font-bold text-cyan-950 hover:text-cyan-900 bg-cyan-100 rounded-full': $route.path === item.route }"
      >
        <div class="flex items-center gap-1">
          <div :class="item.icon" text-l />
          {{ $t(item.label) }}
        </div>
      </router-link>
      <TheSocials class="px-4 text-amber-100" :is-mobile="false" />
      <!-- Language Dropdown -->
      <div class="flex justify-end gap-6 px-20 py-2">
        <a @click="toggleLocales()">
          <div class="cursor-pointer text-2xl text-amber-100 opacity-100 hover:text-cyan-200" i-carbon-language />
        </a>
        <router-link :to="CV.route" class="flex cursor-pointer items-center gap-1 text-2xl text-amber-100 opacity-100 hover:text-cyan-200" :title="CV.label">
          <div :class="CV.icon" />
          <span>{{ $t(CV.label) }}</span>
        </router-link>
      </div>
    </div>
  </nav>
</template>
