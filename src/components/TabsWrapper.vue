<script setup lang="ts">
import { ref, useSlots } from 'vue'

const slots = useSlots()
const tabTitles = slots.default!().map(tab => tab.props?.title)
</script>

<template>
  <div>
    <slot />
  </div>
</template>

<style>
</style>
