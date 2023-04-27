<script setup lang="ts">
import CompositionApi from './components/CompositionApi.vue'
import CompositionApiWithoutEmits from './components/CompositionApiWithoutEmits.vue'
import OptionsApi from './components/OptionsApi.vue'
</script>

<template>
  <div
    :style="{
      display: 'flex',
      alignItems: 'flex-start',
      columnGap: '30px'
    }"
  >
    <CompositionApi />
    <CompositionApiWithoutEmits />
    <OptionsApi />
  </div>
</template>
