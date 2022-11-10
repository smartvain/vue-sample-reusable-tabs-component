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

<style scoped lang="scss">
.tab-content {
  min-height: 400px;
  padding: 20px;
  border-radius: 5px;
  box-shadow: 0 3px 5px 5px rgba(0, 0, 0, 0.05);
}
</style>
