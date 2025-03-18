<script lang="ts" setup>
import Phone from '../icons/Phone.vue';
import Lock from '../icons/Lock.vue';
import Eye from '../icons/Eye.vue';
import { ref, useAttrs } from 'vue';
type InputIcon = 'phone' | 'lock'
type InputType = 'text' | 'password'
const {
  icon,
  type = 'text'
} = defineProps<{
  icon?: InputIcon
  type?: InputType
}>()
const attrs = useAttrs()
const emit = defineEmits<{
  (e: 'change', value: string): void
  (e: 'focus', event: FocusEvent): void
  (e: 'blur', event: FocusEvent): void
}>()
const focused = ref(false)
const viewPass = ref(false)
const handleViewPass = () => {
  viewPass.value = true
}
const handleHidePass = () => {
  viewPass.value = false
}
const handleInput = (e: Event) => {
  emit('change', (e.target as HTMLInputElement).value)
}
const handleFocus = (e: FocusEvent) => {
  focused.value = true
  emit('focus', e)
}
const handleBlur = (e: FocusEvent) => {
  focused.value = false
  emit('blur', e)
}
</script>
<template>
  <div :class="['input-wrapper', {'input-wrapper__focused': focused}]">
    <div class="absolute w-6 h-6 top-0 bottom-0 left-[12px] m-auto flex items-center justify-center">
      <Phone v-if="icon === 'phone'" size="large" />
      <Lock v-else-if="icon === 'lock'" size="large" />
    </div>
    <input
      v-bind="attrs"
      :class="[
        'input',
        {'input__iconed': icon},
        {'input__password': type === 'password'}
      ]"
      :type="type === 'password' && viewPass ? 'text' : type"
      @input="handleInput"
      @focus="handleFocus"
      @blur="handleBlur"
    />
    <div
      v-if="type === 'password'"
      class="absolute w-6 h-6 top-0 bottom-0 right-[12px] m-auto flex items-center justify-center cursor-pointer"
      @click.prevent="handleHidePass"
      @mousedown.prevent="handleViewPass"
      @touchstart="handleViewPass"
      @touchend="handleHidePass"
    >
      <Eye size="large" />
    </div>
  </div>
</template>
<style scoped>
.input-wrapper {
  @apply relative bg-[#F5F6FA] rounded-[18px] overflow-hidden;
}
.input-wrapper svg {
  @apply opacity-50;
}
.input-wrapper__focused {
  @apply bg-[#fff];
}
.input-wrapper__focused:before {
  content: '';
  @apply absolute inset-[0] w-full h-full rounded-[18px] border border-[#257AD7] pointer-events-none;
}
.input-wrapper__focused svg {
  @apply opacity-100 text-[#257AD7];
}
.input {
  @apply w-full h-[58px] px-[12px] outline-none text-[21px] text-[#1D1E20];
}
.input::placeholder {
  @apply text-[#1D1E20/30];
}
.input__iconed {
  @apply pl-[42px];
}
.input__password {
  @apply pr-[42px];
}
</style>