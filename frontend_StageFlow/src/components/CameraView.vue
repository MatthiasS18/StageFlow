<script setup lang="ts">
import { ref } from 'vue'
import Button from 'primevue/button'

const video = ref<HTMLVideoElement | null>(null)
const cameraActive = ref(false)

async function startCamera() {
  try {
    const stream = await navigator.mediaDevices.getUserMedia({
      video: true,
      audio: false
    })

    if (video.value) {
      video.value.srcObject = stream
      cameraActive.value = true
    }
  } catch (error) {
    console.error('Unable to access camera:', error)
  }
}


function stopVideo() {
  if (video.value) {
    const stream = video.value.srcObject as MediaStream | null

    if (stream) {
      stream.getTracks().forEach((track) => {
        track.stop()
      })
    }

    video.value.srcObject = null
  }

  cameraActive.value = false
}


</script>

<template>
  <section class="rounded-xl border border-surface-700 bg-surface-900 p-5">

    <div class="mb-4 flex items-center justify-between">
      <div>
        <span class="text-sm text-surface-400">
          CAMERA
        </span>

        <h2 class="text-xl font-semibold">
          Stage Camera
        </h2>
      </div>

      <span
        class="rounded-full px-3 py-1 text-xs font-semibold"
        :class="cameraActive
          ? 'bg-green-500/15 text-green-400'
          : 'bg-surface-700 text-surface-400'"
      >
        {{ cameraActive ? 'LIVE' : 'OFFLINE' }}
      </span>
    </div>

    <div class="relative aspect-video overflow-hidden rounded-lg bg-black">

      <video
        ref="video"
        autoplay
        playsinline
        class="h-full w-full object-cover"
      ></video>

      <div
        v-if="!cameraActive"
        class="absolute inset-0 flex flex-col items-center justify-center text-center"
      >
        <p class="text-lg font-medium">
          Camera not connected
        </p>

        <p class="mt-1 text-sm text-surface-400">
          Connect a camera to start the stage input.
        </p>
      </div>

      <div
        v-if="cameraActive"
        class="absolute left-4 top-4 flex items-center gap-2 rounded-md bg-black/70 px-3 py-2 text-xs font-semibold text-white"
      >
        <span class="h-2 w-2 rounded-full bg-red-500"></span>
        LIVE
      </div>

    </div>

    <div class="mt-4">
      <Button
        :label="cameraActive ? 'Stop Camera' : 'Start Camera'"
        :icon="cameraActive ? 'pi pi-stop' : 'pi pi-video'"
        :severity="cameraActive ? 'danger' : 'primary'"
        @click="cameraActive ? stopVideo() : startCamera()"
      />
    </div>
  </section>
</template>

<style>

</style>