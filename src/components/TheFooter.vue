<script setup>
const socials = [
  { name: 'Dribbble', icon: 'i-mdi:dribbble', link: 'https://dribbble.com/gabighiur', label: 'socials.dribbble' },
  { name: 'Linkedin', icon: 'i-mdi:linkedin', link: 'https://www.linkedin.com/in/gabighiur/', label: 'socials.linkedin' },
  { name: 'CodePen', icon: 'i-cib:codepen', link: 'https://codepen.io/Gabi-Ghiur', label: 'socials.codepen' },
  { name: 'GitHub', icon: 'i-carbon:logo-github', link: 'https://github.com/gabighiur', label: 'socials.github' },
  { name: 'Instagram', icon: 'i-carbon:logo-instagram', link: 'https://instagram.com/gabi.ghiur', label: 'socials.instagram' },
  { name: 'Sandstorm', icon: 'i-cryptocurrency:sand', link: 'https://app.sandstorm.co/users/0xb4b1205a528a18bbd19928bbd8e5bc38066d05ec', label: 'socials.sandstorm' },
]
</script>

<template>
  <nav class="flex flex-col justify-between bg-cyan-950 p-4 md:flex-row">
    <TheLogo />
    <p class="text-sm font-mono text-white">
      © 2024 Tudor Ghiur
    </p>
    <!-- Social Items -->
    <div class="space-x-4 md:space-x-2">
      <a v-for="social in socials" :key="social.name" :href="social.link" target="_blank" rel="noopener noreferrer" class="text-white">
        <div :class="social.icon" icon-btn hover:bg-amber-100 />
      </a>
    </div>
  </nav>
</template>
