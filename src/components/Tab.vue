<script setup lang="ts">
import { inject } from 'vue'

defineProps({
  'title': {
    type: String
  }
})

const selectedTitle = inject('selectedTitle')
</script>

<template>
  <div class="tab-content" v-show="title == selectedTitle">
    <slot />
  </div>
</template>

<style>
</style>
