<script setup lang="ts">
import type { Event } from '@/type'

defineProps<{
  event: Event
}>()
</script>

<template>
  <div class="event-summary">
    <div class="category">{{ event.category }}</div>
    <div class="organizer">{{ event.organizer }}</div>
  </div>
</template>

<style scoped>
.event-summary {
  text-align: right;
  margin-bottom: 10px;
}

.category,
.organizer {
  font-size: 16px;
}
</style>