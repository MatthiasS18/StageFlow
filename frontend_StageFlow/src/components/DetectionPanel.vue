<script setup lang="ts">
import { ref } from 'vue'
import Card from 'primevue/card'
import Tag from 'primevue/tag'
import Button from 'primevue/button'

const detectionActive = ref(false)

function startDetection() {
  detectionActive.value = true
}

function stopDetection() {
  detectionActive.value = false
}
</script>

<template>
  <div class="flex justify-center">
    <Card class="max-w-sm w-full m-2">
      <template #title>
        Computer Vision
      </template>

      <template #content>
        <div class="flex flex-col items-center gap-4">

          <div class="flex items-center gap-10">
            <span class="w-20">Camera</span>
            <Tag
              severity="success"
              value="● ON"
            />
          </div>

          <div class="flex items-center gap-10">
            <span class="w-20">Detection</span>

            <Tag
              v-if="detectionActive"
              severity="success"
              value="● ON"
            />

            <Tag
              v-else
              severity="danger"
              value="● OFF"
            />
          </div>

          <div class="mt-2">
            <Button
              :label="detectionActive ? 'Stop Detection' : 'Start Detection'"
              :icon="detectionActive ? 'pi pi-stop' : 'pi pi-video'"
              :severity="detectionActive ? 'danger' : 'primary'"
              @click="detectionActive ? stopDetection() : startDetection()"
            />
          </div>

        </div>
      </template>
    </Card>
  </div>
</template>

<style>
</style>