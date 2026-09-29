<script setup lang="ts">
import { ref } from 'vue'
import Card from 'primevue/card'
import Tag from 'primevue/tag'
import Button from 'primevue/button'

const effectActive = ref(false)
const currentEffect = ref('Blue Pulse')

function triggerEffect() {
  effectActive.value = true
}

function stopEffect() {
  effectActive.value = false
}
</script>

<template>
  <div class="flex justify-center">
    <Card class="w-full max-w-sm m-2">
      <template #title>
        Visual Effect
      </template>

      <template #content>
        <div class="flex flex-col gap-4">

          <!-- Current effect -->
          <div class="flex items-center justify-between">
            <span class="font-medium">
              Current effect
            </span>

            <Tag
              severity="info"
              :value="currentEffect"
            />
          </div>

          <!-- Status -->
          <div class="flex items-center justify-between">
            <span class="font-medium">
              Status
            </span>

            <Tag
              :severity="effectActive ? 'success' : 'secondary'"
              :value="effectActive ? '● Active' : '● Inactive'"
            />
          </div>

          <!-- Controls -->
          <div class="flex flex-col gap-2">

            <Button
              label="Trigger Effect"
              icon="pi pi-bolt"
              :disabled="effectActive"
              @click="triggerEffect"
            />

            <Button
              label="Stop Effect"
              icon="pi pi-stop"
              severity="secondary"
              outlined
              :disabled="!effectActive"
              @click="stopEffect"
            />

          </div>

        </div>
      </template>
    </Card>
  </div>
</template>

<style>
</style>