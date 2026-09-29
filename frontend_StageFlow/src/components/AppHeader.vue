<script setup lang="ts">
import Button from 'primevue/button'
import Tag from 'primevue/tag'
</script>

<template>
  <header class="flex items-center justify-between px-6 py-4">
    <div class="flex items-center gap-3">
      <div class="flex h-10 w-10 items-center justify-center rounded-lg bg-primary text-white font-bold">
        SF
      </div>

      <div>
        <h1 class="text-xl font-bold">StageFlow</h1>
        <p class="text-sm text-surface-500">
          Interactive Stage Platform
        </p>
      </div>
    </div>

    <div class="flex items-center gap-3">
      <Tag value="System Online" severity="success" />

      <Button
        label="Settings"
        icon="pi pi-cog"
        severity="secondary"
        outlined
      />
    </div>
  </header>
</template>

<style>

</style>