<template>
    <ul class='nav__tabs'>
        <slot />
    </ul>
</template>
<script setup lang="ts">
</script>

<style lang="scss">
.nav__tabs {
    border-bottom: 1px solid #e7eaf0;
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
    color: #525f7f;
    font-weight: 500;
    font-size: 0.875rem;
    font-family: Inter, ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Helvetica Neue, Arial, Noto Sans, Liberation Sans, sans-serif, Apple Color Emoji, Segoe UI Emoji, Segoe UI Symbol, Noto Color Emoji;


    .tabs__item {
        padding: 1.25rem;
        padding-top: 0.5rem;
        cursor: pointer;
    }

    .tabs__item:hover {
        color: #5c60f5;
        cursor: pointer;
    }

    .tabs__item.active {
        color: #5c60f5;
        border-bottom: 1px solid #5c60f5;
    }
}</style>