<script>
export default {
  data() {
    return {
      letters: ['t', 'u', 'd', 'o', 'r', 'g', 'h', 'i', 'u', 'r'],
    }
  },
  mounted() {
    this.startWaveAnimation()
  },
  methods: {
    startWaveAnimation() {
      this.$refs.letters.forEach((letter, index) => {
        setTimeout(() => {
          letter.classList.add('wave-animate')
          letter.style.animationDelay = `${index * 100}ms`
        }, index * 100)
      })
    },
  },
}
</script>

<template>
  <div>
    <span v-for="(letter, index) in letters" :key="index" ref="letters" class="inline-block text-amber-100">
      {{ letter }}
    </span>
  </div>
</template>

<style scoped>
@keyframes waveAnimation {
  0% {
    transform: translateY(0);
  }
  20% {
    transform: translateY(-10px);
  }
  40%, 100% {
    transform: translateY(0);
  }
}

.wave-animate {
  animation: waveAnimation 2s ease-in-out infinite;
  transition: transform 0.3s ease-in-out;
}
</style>
