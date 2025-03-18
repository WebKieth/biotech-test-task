<script lang="ts" setup>
type ButtonVariant = 'filled' | 'outlined'
const {
  variant = 'filled'
} = defineProps<{
  variant?: ButtonVariant
}>()
const emit = defineEmits<{
  (e: 'click', event: MouseEvent): void
}>()
</script>
<template>
  <button :class="['button', `button__${variant}`]" @click="(e) => emit('click', e)">
    <slot />
  </button>
</template>
<style scoped>
.button {
  @apply inline-flex items-center justify-center px-[12px] h-[58px] rounded-[18px] text-[18px];
}
.button__filled {
  @apply bg-[#257AD7] text-[#fff] hover:bg-[#2378D5] active:bg-[#2075D2];
}
.button__outlined {
  @apply bg-[#fff] text-[#257AD7] relative hover:text-[#2378D5] active:text-[#2075D2];
}
.button__outlined:hover::before {
  @apply border-[#2378D5]
}
.button__outlined:active::before {
  @apply border-[#2075D2]
}
.button__outlined::before {
  content: '';
  @apply absolute pointer-events-none m-auto inset-[0] border border-[#257AD7] rounded-[18px] ;
}
</style>