<template>
    <div
        class="dropdown"
        tabindex="-1"
        @blur.capture="$emit('blur')"
        @focus.capture="$emit('focus')"
    >
        <div class='dropdown-menu-button'>
            <slot name="body" />
        </div>
        <div
            class='dropdown-menu'
            v-if="isShow"
        >
            <slot name="drop"/>
        </div>
    </div>
</template>
<script setup lang="ts">

interface Props {
    isShow?: boolean
}

defineEmits(["click"])
defineProps<Props>()

</script>

<style lang="scss">

</style>