<script setup lang="ts">
useHead({
  title: 'Tudor',
  meta: [
    { name: 'description', content: 'UI/UX Developer' },
    {
      name: 'theme-color',
      content: () => isDark.value ? '#00aba9' : '#ffffff',
    },
  ],
  link: [
    {
      rel: 'icon',
      type: 'image/png',
      href: () => preferredDark.value ? '/fav.png' : '/fav.png',
    },
  ],
})
</script>

<template>
  <RouterView />
</template>
