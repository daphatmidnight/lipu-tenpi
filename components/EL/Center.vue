<template>
  <component
    :is="tag"
    :class="[
      $style.center,
      andText ? $style.andText : '',
      intrinsic ? $style.intrinsic : ''
    ]"
    :style="{
      '--max': max,
      '--gutters': gutters
    }">
    <slot />
  </component>
</template>

<script lang="ts" setup>
  withDefaults(
    defineProps<{
      tag?: string
      max?: string
      andText?: boolean
      gutters?: string
      intrinsic?: boolean
    }>(),
    {
      tag: "div",
      max: "var(--measure)",
      andText: false,
      gutters: "0",
      intrinsic: false
    }
  )
</script>

<style module>
  .center {
    box-sizing: content-box;
    margin-inline: auto;
    max-inline-size: var(--max, var(--measure));
    padding-inline-start: var(--gutters, 0);
    padding-inline-end: var(--gutters, 0);
  }

  .center.andText {
    text-align: center;
  }

  .center.intrinsic {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>
