<script setup lang="ts">
import { ref } from 'vue'

const copied = ref(false)
function downloadCV() {
  const cvUrl = '/assets/cv.pdf'
  const anchorElement = document.createElement('a')
  anchorElement.href = cvUrl
  anchorElement.download = 'cv.pdf'
  anchorElement.click()
}
function sendEmail() {
  const email = 'tudor.ghiur@yahoo.com'
  const subject = encodeURIComponent('Subject')
  const body = encodeURIComponent('Body')
  const mailtoLink = `mailto:${email}?subject=${subject}&body=${body}`
  window.location.href = mailtoLink
}

function copyEmail() {
  const emailInput = document.getElementById('emailInput') as HTMLInputElement
  emailInput.select()
  document.execCommand('copy')

  copied.value = true

  setTimeout(() => {
    copied.value = false
  }, 2000)
}
</script>

<template>
  <div min-h-screen flex items-center justify-center rounded bg-emerald-100 px-4 lg:px-20 md:px-10>
    <div flex flex-col items-center justify-center gap-4 rounded-12 bg-cyan-900 p-6 lg:p-20 md:p-10>
      <div text-left text-2xl text-white>
        <div>
          <div flex flex-col items-center>
            <h3>{{ $t('cv.title') }} </h3>
            <div i-mdi:arrow-down text-4xl />
          </div>
          <div flex items-center justify-center gap-4 p-2>
            <input id="emailInput" type="text" value="tudor.ghiur@yahoo.com" readonly class="rounded-md bg-gray-2 p-4 text-xl text-cyan-950">
          </div>
        </div>
      </div>
      <div flex flex-row items-center gap-4>
        <button class="flex gap-2 btn" @click="downloadCV">
          <div i-mdi:download />
          <span>{{ $t('cv.download') }}</span>
        </button>
        <button class="flex gap-2 btn" @click="sendEmail">
          <div i-mdi:email />
          <span>{{ $t('cv.send') }}</span>
        </button>
        <div flex flex-row>
          <button class="flex gap-2 btn" @click="copyEmail">
            <div i="mdi-content-copy" />
            <span>{{ $t('cv.copy') }}</span>
          </button>
          <div v-if="copied" class="animate-fadeOut absolute rounded-md bg-white px-4 py-2 text-cyan-950">
            Copied
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

  <style>
    @keyframes fadeOut {
    from {
    opacity: 1;
    }
    to {
    opacity: 0;
    }
    }
    .animate-fadeOut {
    animation: fadeOut 2s ease-out forwards;
    }
  </style>
