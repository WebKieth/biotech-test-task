<script lang="ts" setup>
import Chevron from './icons/Chevron.vue';


</script>
<template>
  <div class="w-full h-[115px] pt-[53px] px-6 flex items-center justify-between border-b border-black/10">
    <div class="w-1/3">
      <Chevron />
    </div>
    <div class="w-1/3 flex justify-center font-semibold text-[22px]">Вход</div>
    <div class="w-1/3 flex justify-end">
      <div class="flex items-center gap-2.5">
        <span class="font-light text-[22px] uppercase">
          ru
        </span>
        <Chevron class="rotate-270" />
      </div>
    </div>
  </div>
</template>