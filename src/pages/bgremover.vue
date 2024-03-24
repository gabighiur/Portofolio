<script>
/* eslint no-undef: "error" */
import process from 'node:process'
import axios from 'axios'
import logo from '~/assets/bgremover.png'
import img1 from '~/assets/img1.jpg'
import img2 from '~/assets/img2.png'

export default {
  data() {
    return {
      imageUrl: null,
      previewImage: null,
      imageFile: null,
      loading: false,
      selectedTab: 'original',
      logo,
      img1,
      img2,
    }
  },
  methods: {
    goBack() {
      window.history.back()
    },
    async handleFileChange(event) {
      const file = event.target.files[0]

      if (file) {
        this.previewImage = URL.createObjectURL(file)
        this.imageFile = file
      }
    },
    async removeBackground() {
      if (this.imageFile) {
        this.loading = true
        const formData = new FormData()
        formData.append('image_file', this.imageFile)

        try {
          const response = await axios.post('https://api.removal.ai/3.0/remove', formData, {
            headers: {
              'Rm-Token': process.env.VUE_APP_API_TOKEN,
              'Content-Type': 'multipart/form-data',
            },
            params: {
              get_file: 1,
            },
          })

          if (response.data && response.data.url) {
            this.imageUrl = response.data.url
            this.selectTab('processed')
          }
          else {
            console.error('Invalid response data:', response.data)
          }
        }
        catch (error) {
          console.error('Error processing image:', error)
        }
        finally {
          this.loading = false
        }
      }
      else {
        console.error('No image file selected.')
      }
    },
    downloadImage() {
      const link = document.createElement('a')
      link.href = this.imageUrl
      link.download = 'processed_image.png'
      document.body.appendChild(link)
      link.click()
      document.body.removeChild(link)
    },
    selectTab(tab) {
      this.selectedTab = tab
    },
  },
}
</script>

<template>
  <section class="min-h-screen flex flex-col items-center justify-center gap-8 bg-orange-200 p-8 lg:flex-row">
    <!-- Header -->
    <header>
      <div class="sedonaText p-4 text-left">
        <div class="flex gap-4">
          <img :src="logo" class="mb-4 w-20">
          <div>
            <h1 class="text-6xl text-cyan-950 lg:text-7xl md:text-7xl sm:text-7xl">
              BG Remover
            </h1>
            <p class="ml-2 text-xl text-cyan-950 md:text-2xl">
              The magic of AI
            </p>
          </div>
        </div>
      </div>
    </header>
    <!-- Container -->
    <div v-if="!previewImage" class="rounded-lg bg-white p-4">
      <!-- File Input -->
      <div class="mb-4">
        <input class="p-4 text-gray-700" type="file" @change="handleFileChange">
      </div>
    </div>

    <div v-if="previewImage" class="rounded-lg bg-white p-8">
      <!-- Tabs Navigation -->
      <div class="mb-4">
        <ul class="flex">
          <li class="mr-2">
            <button :class="{ 'border-b-2 border-teal-700': selectedTab === 'original' }" @click="selectTab('original')">
              Original
            </button>
          </li>
          <li>
            <button v-if="imageUrl" :class="{ ' border-b-2 border-teal-700': selectedTab === 'processed' }" @click="selectTab('processed')">
              Processed
            </button>
          </li>
        </ul>
      </div>

      <!-- Image Container -->
      <div class="flex flex-col items-center justify-center">
        <div v-if="selectedTab === 'original'">
          <img :src="previewImage" alt="Original Image" class="mb-2 h-auto max-w-60">
        </div>
        <div v-if="selectedTab === 'processed'" class="relative">
          <!-- Loading Indicator during upload -->
          <div v-if="loading" class="absolute left-0 top-0 h-full w-full flex items-center justify-center bg-gray-800 bg-opacity-50">
            <span class="text-white">Uploading...</span>
          </div>
          <!-- Display the processed image -->
          <img v-if="imageUrl" :src="imageUrl" alt="Processed Image" class="mb-2 h-auto max-w-60">
        </div>
      </div>

      <!-- Action Buttons -->
      <div class="mt-4 flex flex-col items-center md:flex-row md:justify-center">
        <!-- "Remove Background" button will only appear after an image has been uploaded -->
        <button v-if="previewImage && !imageUrl" class="mb-2 rounded bg-teal-700 px-4 py-2 font-bold text-white md:mb-0 md:mr-2 hover:bg-teal-500" @click="removeBackground">
          Remove Background
        </button>
        <!-- "Download" button -->
        <button v-if="imageUrl" class="flex rounded bg-gray-300 px-4 py-2 font-bold text-gray-800 hover:bg-gray-400" @click="downloadImage">
          <svg class="mr-2 h-4 w-4 fill-current" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
            <path d="M13 8V2H7v6H2l8 8 8-8h-5zM0 18h20v2H0v-2z" />
          </svg>
          <span>Download</span>
        </button>
      </div>
    </div>
  </section>

  <section class="flex flex-col items-center justify-center gap-8 bg-gray-800 p-8">
    <h2 class="text-3xl font-black text-orange-200">
      {{ $t('bg.title') }}
    </h2>
    <p class="text-lg text-orange-200">
      {{ $t('bg.desc') }}
    </p>
    <!-- Example Container -->
    <div class="bg-gray-900 p-4">
      <div class="flex flex-row gap-8">
        <img :src="img1" class="h-auto w-50 rounded-2xl">
        <img :src="img2" class="h-auto w-50 rounded-2xl">
      </div>
    </div>
    <div class="flex flex-row items-center gap-8">
      <button class="copper cursor-pointer rounded px-4 py-2 font-bold text-orange-950 hover:bg-orange-300" @click="goBack">
        {{ $t('button.back') }}
      </button>
    </div>
  </section>
</template>
