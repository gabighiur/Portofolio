<script setup lang="ts">
import { useI18n } from 'vue-i18n'
import { availableLocales, loadLanguageAsync } from '~/modules/i18n'

const { t, locale } = useI18n()

const HOME = { label: t('nav.item1'), route: '/', section: '' }
const WORK = { label: t('nav.item2'), route: '/section2', section: '' }
const ABOUT = { label: t('nav.item3'), route: '/section3', section: '' }
const CV = { label: t('nav.item4'), route: '/cv', section: '' }

const NAV_ITEMS = [HOME, WORK, ABOUT, CV]

async function toggleLocales() {
  const locales = availableLocales
  const newLocale = locales[(locales.indexOf(locale.value) + 1) % locales.length]
  await loadLanguageAsync(newLocale)
  locale.value = newLocale
}
</script>

<template>
  <nav sticky top-0 flex items-center justify-center bg-cyan-950 p-4 px-20>
    <!-- Items Section -->
    <div flex flex-row cursor-pointer items-center text-4xl>
      <router-link
        v-for="item in NAV_ITEMS"
        :key="item.label"
        :to="item.route"
        class="px-4 py-2 text-amber100 hover:text-cyan-200"
        :class="{ 'font-bold text-cyan-950 hover:text-cyan-900 bg-cyan-100 rounded-full': $route.path === item.route }"
      >
        {{ item.label }}
      </router-link>
      <TheSocials class="text-amber-100" :is-mobile="false" />
      <!-- Language Dropdown -->
      <div class="flex justify-end px-20 py-2 text-amber-100 hover:text-cyan-200">
        <a :title="t('button.toggle_langs')" @click="toggleLocales()">
          <div class="cursor-pointer text-2xl opacity-100" i-carbon-language />
        </a>
      </div>
    </div>
  </nav>
</template>
