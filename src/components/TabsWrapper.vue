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
        :class="{ selected: title == selectedTitle }"
        @click="selectedTitle = title"
      >
        {{ title }}
      </li>
    </ul>
    <slot />
  </div>
</template>

<style scoped lang="scss">
.tabs {
  max-width: 480px;
  margin: 0 auto;
}

.tabs-header {
  margin-bottom: 10px;
  list-style: none;
  padding: 0;
  display: flex;
}

.tabs-header li {
  width: 80px;
  text-align: center;
  padding: 10px 20px;
  margin-right: 10px;
  background-color: #ddd;
  border-radius: 5px;
  cursor: pointer;
  transition: 0.4s all ease;
  color: darken($color: #000, $amount: 0);
}

.tabs-header li.selected {
  background-color: #0984e3;
  color: white;
}
</style>
