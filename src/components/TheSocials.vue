<script>
export default {
  data() {
    return {
      socialLinks: [
        { name: 'Dribbble', icon: 'i-mdi:dribbble', link: 'https://dribbble.com/gabighiur', label: 'socials.dribbble' },
        { name: 'Linkedin', icon: 'i-mdi:linkedin', link: 'https://www.linkedin.com/in/gabighiur/', label: 'socials.linkedin' },
        { name: 'CodePen', icon: 'i-cib:codepen', link: 'https://codepen.io/Gabi-Ghiur', label: 'socials.codepen' },
        { name: 'GitHub', icon: 'i-carbon-logo-github', link: 'https://github.com/gabighiur', label: 'socials.github' },
        { name: 'Instagram', icon: 'i-carbon-logo-instagram', link: 'https://instagram.com/gabi.ghiur', label: 'socials.instagram' },
        { name: 'Sandstorm', icon: 'i-cryptocurrency:sand', link: 'https://app.sandstorm.co/users/0xb4b1205a528a18bbd19928bbd8e5bc38066d05ec', label: 'socials.sandstorm' },
      ],
      panel: null,
    }
  },
  methods: {
    showPanel() {
      this.panel = this.$refs.socialPanel
      const contentHeight = `${this.panel.scrollHeight}px`
      this.panel.style.maxHeight = contentHeight
      this.panel.style.opacity = '1'
    },

    hidePanel() {
      if (this.panel) {
        this.panel.style.opacity = '0'
        this.panel.addEventListener('transitionend', this.handleTransitionEnd)
      }
    },

    handleTransitionEnd() {
      this.panel.style.maxHeight = '0'
      this.panel.removeEventListener('transitionend', this.handleTransitionEnd)
    },

    openLink(url) {
      window.open(url, '_blank')
    },
  },
}
</script>

<template>
  <div class="group relative" @click="showPanel" @mouseleave="hidePanel">
    <span><p cursor-pointer hover:text-cyan-200>socials</p></span>
    <div
      ref="socialPanel"
      class="social-panel absolute left-1/2 w-auto flex flex-col overflow-hidden rounded-2xl bg-cyan-950 p-4 text-left opacity-1 transition-max-height duration-400 ease-out"
    >
      <a
        v-for="link in socialLinks"
        :key="link.name"
        class="flex flex-row gap-4 text-2xl font-sans ease-in icon-btn hover:text-emerald-100"
        rel="noreferrer"
        :href="link.link"
        @click.prevent="openLink(link.link)"
      >
        <div :class="link.icon" />
        <span>{{ $t(link.label) }}</span>
      </a>
    </div>
  </div>
</template>

<style scoped>
.social-panel {
  transform: translateX(-50%);
}
</style>
