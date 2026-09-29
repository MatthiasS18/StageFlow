<script setup lang="ts">
import { ref } from 'vue'
import Card from 'primevue/card'
import Tag from 'primevue/tag'

const peopleDetected = ref(3)
const movementDetected = ref(true)
const effectActive = ref(true)
</script>

<template>
  <div class="flex justify-center">
    <Card class="w-full max-w-sm">
      <template #title>
        Live Metrics
      </template>

      <template #content>
        <div class="flex flex-col gap-4">

          <div class="flex items-center justify-between">
            <span class="font-medium">
              People
            </span>

            <Tag
              :severity="peopleDetected > 0 ? 'success' : 'secondary'"
              :value="`${peopleDetected} detected`"
            />
          </div>

          <div class="flex items-center justify-between">
            <span class="font-medium">
              Movement
            </span>

            <Tag
              :severity="movementDetected ? 'success' : 'secondary'"
              :value="movementDetected ? 'Detected' : 'None'"
            />
          </div>

          <div class="flex items-center justify-between">
            <span class="font-medium">
              Effect
            </span>

            <Tag
              :severity="effectActive ? 'info' : 'secondary'"
              :value="effectActive ? 'Active' : 'Inactive'"
            />
          </div>

        </div>
      </template>
    </Card>
  </div>
</template>

<style>
</style>