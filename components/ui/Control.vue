<template>
  <div
      class="control"
      :class="[{ invalid }, { valid }, { control__hideMessage: hideMessage }]"
  >
    <div
        v-if="label"
        class="control__label"
    >
      {{ label }}
    </div>
    <div class="control__wrap">
      <slot />
      <div
          v-if="rightIcon"
          class="control__icon"
      >
        <component :is="rightIcon" />
      </div>
      <div
          v-if="$slots.rightIcon"
          class="control__icon"
      >
        <slot name="rightIcon" />
      </div>
    </div>
    <div
        class="control__message"
        v-if="message"
        :class="[{ show: !!message }]"
    >
      {{ message }}
    </div>
  </div>
</template>

<script setup lang="ts">
defineComponent({
  inheritAttrs: false,
});

import { InputHTMLAttributes } from "nuxt/dist/app/compat/capi";

interface Props extends /* @vue-ignore */ InputHTMLAttributes {
  label?: string;
  rightIcon?: any;
  message?: any;
  invalid?: boolean;
  valid?: boolean;
  hideMessage?: boolean
}

defineProps<Props>();
</script>

<style lang="scss"></style>
