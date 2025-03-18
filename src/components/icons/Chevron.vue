<script lang="ts" setup>
import { sizes } from './constants';
import { type IconSize } from './types';
const { size = 'medium' } = defineProps<{
  size?: IconSize
}>()
const currentSize = sizes[size]
</script>
<template>
  <svg :style="{width: currentSize, height: currentSize}" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M6.04155 9.99995C6.04077 9.83407 6.10685 9.67486 6.22488 9.55829L12.8916 2.89162C13.1378 2.66215 13.5216 2.66893 13.7596 2.90694C13.9976 3.14495 14.0043 3.5287 13.7749 3.77495L7.54988 9.99995L13.7749 16.225C14.0043 16.4712 13.9976 16.855 13.7596 17.093C13.5216 17.331 13.1378 17.3378 12.8915 17.1083L6.22488 10.4416C6.10685 10.3251 6.04077 10.1658 6.04155 9.99995Z" fill="currentColor"/>
  </svg>

</template>