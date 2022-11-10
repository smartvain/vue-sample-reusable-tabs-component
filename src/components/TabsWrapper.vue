<script setup lang="ts">
import { ref, provide, useSlots } from 'vue'

const slots = useSlots()
const tabTitles = ref(slots.default!().map(tab => tab.props?.title))
const selectedTitle = ref(tabTitles.value[0])

provide('selectedTitle', selectedTitle)
</script>

<template>
  <div class="tabs">
    <ul class="tabs-header">
      <li
        v-for="title in tabTitles"
        :key="title"
        @click="selectedTitle = title"
      >
        {{ title }}
      </li>
    </ul>
    <slot />
  </div>
</template>

<style>
</style>
