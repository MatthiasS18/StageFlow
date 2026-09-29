<script setup lang="ts">
import { ref } from 'vue'
import Button from 'primevue/button'
import AppHeader from '@/components/AppHeader.vue'
import CameraView from '@/components/CameraView.vue'
import DetectionPanel from '@/components/DetectionPanel.vue'
import MetricsPanel from '@/components/MetricsPanel.vue'
import EffectPanel from '@/components/EffectPanel.vue'

</script>

<template>
  <div class="min-h-screen">
    <AppHeader />

    <main class="p-6">
      <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">

        <div class="lg:col-span-2">
          <CameraView />
        </div>

        <div class="flex flex-col gap-6">
          <DetectionPanel />
          <MetricsPanel />
          <EffectPanel />
        </div>

      </div>
    </main>
  </div>
</template>

<style scoped>

</style>