<template>
    <div
        class="dropdown"
        tabindex="-1"
        @blur.capture="isShow = false"
        @focus.capture="isShow = true"
    >
        <div class='dropdown-menu-button'>
            <slot name="body" />
        </div>
        <div
            class='dropdown-menu'
            v-if="isShow"
        >
            <slot name="drop"></slot>
        </div>
    </div>
</template>
<script setup lang="ts">

const isShow = ref(false)

</script>

<style>

</style>