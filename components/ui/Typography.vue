<template>
    <div
        class="typography"
        :class="[
            `typography-size-${fontSize}`,
            `typography-weight-${fontWeight}`,
            `typography-color-${color}`,
            `typography-text-wrap-${textWrap}`,
            `typography-text-align-${textAlign}`
        ]"
    >
        <slot />
    </div>
</template>
<script setup lang="ts">
interface Props {
    fontSize?: "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"
    fontWeight?: "bold" | "regular" | "light" | "medium"
    color?: "blue" | "black" | "white" | "gray" | "primary"
    textWrap?: "no-wrap"
    textAlign?: "right" | "left"
}
defineProps<Props>()
</script>

<style lang="scss">
.typography {
    font-size: 16px;
    display: inline;
    color: #16192C;
    font-family: Inter, ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Helvetica Neue, Arial, Noto Sans, Liberation Sans, sans-serif, Apple Color Emoji, Segoe UI Emoji, Segoe UI Symbol, Noto Color Emoji;

    .typography-text-wrap-no-wrap {
        white-space: nowrap;
    }

    &-text-align-right {
        text-align: right;
    }

    &-color-gray {
        color: gray;
    }

    &-color-blue {
        color: #2805FF;
    }

    &-color-white {
        color: white;
    }

    &-color-primary {
        color: #133674;
    }

    &-size-1 {
        font-size: 10px;
    }

    &-size-2 {
        font-size: 12px;
    }

    &-size-3 {
        font-size: 14px;
    }

    &-size-4 {
        font-size: 16px;
    }

    &-size-5 {
        font-size: 18px;
    }

    &-size-6 {
        font-size: 20px;
    }

    &-size-7 {
        font-size: 24px;
    }

    &-size-8 {
        font-size: 28px;
    }

    &-size-9 {
        font-size: 32px;
    }

    &-weight-bold {
        font-weight: 700;
    }

    &-weight-medium {
        font-weight: 500;
    }
}
</style>