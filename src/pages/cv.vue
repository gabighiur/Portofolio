<script setup lang="ts">
import { ref } from 'vue'

// Reactive variable to control the visibility of the "Copied" message
const copied = ref(false)

// Function to handle sending an email
function sendEmail() {
  // Generate mailto link and open default email client
  const email = 'tudor.ghiur@yahoo.com'
  const subject = encodeURIComponent('Subject')
  const body = encodeURIComponent('Body')
  const mailtoLink = `mailto:${email}?subject=${subject}&body=${body}`
  window.location.href = mailtoLink
}

// Function to handle copying the email address
function copyEmail() {
  const emailInput = document.getElementById('emailInput') as HTMLInputElement
  emailInput.select()
  document.execCommand('copy')
  // Update the flag to show the "Copied" message
  copied.value = true
  // Hide the "Copied" message after 2 seconds
  setTimeout(() => {
    copied.value = false
  }, 2000)
}
</script>

<template>
  <div min-h-screen flex items-center justify-center rounded bg-emerald-100 px-4 lg:px-20 md:px-10>
    <div flex flex-col items-center justify-center gap-4 rounded-12 bg-cyan-900 p-6 lg:p-20 md:p-10>
      <div i-carbon-warning inline-block text-6xl />
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
        <button class="flex gap-2 btn" @click="sendEmail">
          <div i-mdi:email />
          <span>{{ $t('cv.send') }}</span>
        </button>
        <div flex flex-row>
          <button class="flex gap-2 btn" @click="copyEmail">
            <div i="mdi-content-copy" />
            <span>{{ $t('cv.copy') }}</span>
          </button>
          <!-- Conditionally render the "Copied" message -->
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
