<script setup lang="ts">
import { computed, ref } from 'vue'
import { useI18n } from 'vue-i18n'
import { availableLocales, loadLanguageAsync } from '~/modules/i18n'

const { t, locale } = useI18n()
const menuOpen = ref(false)
const hamburgerLine = 'h-0 w-6 border-t-4 rounded border-amber-100 mt-1'

const HOME = { label: t('nav.item1'), route: '/', section: '' }
const WORK = { label: t('nav.item2'), route: '/portofolio', section: '' }
const ABOUT = { label: t('nav.item3'), route: '/info', section: '' }
const CV = { label: t('nav.item4'), route: '/cv', section: '' }

const socialLinks = [
  { name: 'Dribbble', icon: 'i-mdi:dribbble', link: 'https://dribbble.com/gabighiur', label: 'socials.dribbble' },
  { name: 'Linkedin', icon: 'i-mdi:linkedin', link: 'https://www.linkedin.com/in/gabighiur/', label: 'socials.linkedin' },
  { name: 'CodePen', icon: 'i-cib:codepen', link: 'https://codepen.io/Gabi-Ghiur', label: 'socials.codepen' },
  { name: 'GitHub', icon: 'i-carbon-logo-github', link: 'https://github.com/gabighiur', label: 'socials.github' },
  { name: 'Instagram', icon: 'i-carbon-logo-instagram', link: 'https://instagram.com/gabi.ghiur', label: 'socials.instagram' },
  { name: 'Sandstorm', icon: 'i-cryptocurrency:sand', link: 'https://app.sandstorm.co/users/0xb4b1205a528a18bbd19928bbd8e5bc38066d05ec', label: 'socials.sandstorm' },
]

async function toggleLocales() {
  const locales = availableLocales
  const newLocale = locales[(locales.indexOf(locale.value) + 1) % locales.length]
  await loadLanguageAsync(newLocale)
  locale.value = newLocale
}

const nonHamburgerItems = computed(() => {
  return [HOME, WORK, ABOUT]
})

const mobileMenuItems = computed(() => {
  return [CV]
})
</script>

<template>
  <nav :class="{ 'sticky z-10 top-0 max-h-20 overflow-hidden': !menuOpen, 'sticky z-10 top-0 transition-all duration-600 ease-in': menuOpen }" class="flex items-center justify-between bg-cyan-950 p-4">
    <!-- Non-Hamburger Menu Items -->
    <div class="gap-4 text-amber-100 md:flex">
      <router-link
        v-for="item in nonHamburgerItems"
        :key="item.label"
        :to="item.route"
        class="px-4 py-2 text-2xl text-amber-100"
        :class="{ 'font-bold text-cyan-950 bg-cyan-100 rounded-full': $route.path === item.route }"
      >
        {{ item.label }}
      </router-link>
    </div>

    <!-- Mobile Navbar -->
    <div v-if="menuOpen" class="fixed left-0 top-0 w-full flex flex-col items-center gap-4 bg-cyan-950 py-4 text-4xl">
      <!-- Mobile Menu Items -->
      <router-link
        v-for="item in mobileMenuItems"
        :key="item.label"
        :to="item.route"
        class="py-2 text-amber-100 hover:text-cyan-200"
        @click="menuOpen = false"
      >
        {{ item.label }}
      </router-link>
      <!-- Language Dropdown -->
      <a :title="t('button.toggle_langs')" class="py-2 text-2xl text-amber-100 hover:text-cyan-200" @click="toggleLocales(); menuOpen = false">
        <div flex flex-row gap-4>
          <div class="cursor-pointer" i-carbon-language />
          <span>Change language</span>
        </div>
      </a>
      <!-- Social Links -->
      <div class="flex gap-4 py-2">
        <a
          v-for="link in socialLinks"
          :key="link.name"
          :href="link.link"
          class="text-amber-100 hover:text-cyan-200"
        >
          <div :class="link.icon" class="text-xl" />
        </a>
      </div>

      <div>
        <TheLogo />
      </div>
      <hr min-w-sm border-1 border-emerald-100>
    </div>

    <!-- Hamburger Button -->
    <button class="group h-11 w-11 flex flex-col items-end justify-center md:hidden" @click="menuOpen = !menuOpen">
      <div :class="`${hamburgerLine} ${menuOpen ? 'rotate-45 translate-y-1 opacity-100 group-hover:opacity-100 transition-transform duration-300' : 'opacity-100 group-hover:opacity-100'}`" />
      <div :class="`${hamburgerLine} ${menuOpen ? 'opacity-0' : 'opacity-100 group-hover:opacity-100'}`" />
      <div :class="`${hamburgerLine} ${menuOpen ? '-rotate-45 -translate-y-3 opacity-100 group-hover:opacity-100 transition-transform duration-300' : 'opacity-100 group-hover:opacity-100'}`" />
    </button>
  </nav>
</template>
