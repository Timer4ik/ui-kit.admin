

<template>
  <button
      class="button"
      v-bind="$attrs"
      :class="(color ? ' button-' + color : ' button-primary')"
  >
    <slot></slot>
  </button>
</template>

<script setup lang="ts" >
import { ButtonHTMLAttributes } from "vue"

defineComponent({
  inheritAttrs: false
})

interface Props extends /* @vue-ignore */ ButtonHTMLAttributes {

  color?: "standard" | "primary" | "danger" | "green";
}

defineProps<Props>();
</script>

<style  lang="scss">
.button {
    font-family: Inter, ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", "Liberation Sans", sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
    display: inline-block;
    font-weight: 500;
    line-height: 1.3;
    color: #525f7f;
    text-align: center;
    vertical-align: middle;
    cursor: pointer;
    -webkit-user-select: none;
    -moz-user-select: none;
    user-select: none;
    background-color: rgba(0, 0, 0, 0);
    border: 1px solid rgba(0, 0, 0, 0);
    padding: .75rem 1.25rem;
    font-size: 1rem;
    border-radius: .375rem;
    transition: color .15s ease-in-out, background-color .15s ease-in-out, border-color .15s ease-in-out, box-shadow .15s ease-in-out;
    &.button-primary {
        color: #fff;
        background-color: #5c60f5;
        border-color: #5c60f5;
        box-shadow: 0 1px 1px rgba(0, 0, 0, .075);
        &:hover {
            background-color: #4a4dc4;
        }
        &:focus {
            background-color: #4a4dc4;
            box-shadow: 0 0 0 3px rgba(92, 96, 245, 0.25);
        }
    }
    &.button-standard {
        color: #16192c;
        background-color: white;
        border: 1px solid #e7eaf0;
        &:hover {
            background-color: #E7EAF0;
        }
        &:focus {
            background-color: #E7EAF0;
            box-shadow: 0 1px 1px rgba(0, 0, 0, .075), 0 0 0 3px rgba(200, 203, 211, .5);
        }
    }
    &.button-danger {
        background-color: #f36;
        border-color: #f36;
        color: white;
        box-shadow: 0 1px 1px rgba(0, 0, 0, .075);
        &:hover {
            background-color: #cc2952;
        }
        &:focus {
            background-color: #cc2952;
            box-shadow: 0 1px 1px rgba(0, 0, 0, .075), 0 0 0 3px rgba(255, 82, 125, .5);
        }
    }
    &.button-green {
        background-color: #10A662;
        border-color: #10A662;
        color: white;
        box-shadow: 0 1px 1px rgba(0, 0, 0, .075);
        &:hover {
            background-color: #10A662;
        }
        &:focus {
            background-color: #10A662;
            box-shadow: 0 1px 1px rgba(0, 0, 0, .075), 0 0 0 3px rgba(53, 177, 69, 0.5);
        }
    }
    padding: .5rem 1rem;
    font-size: 0.875rem;
    border-radius: .375rem;
}
</style>