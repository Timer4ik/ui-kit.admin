<template>
    <div
        class="dropdown"
        tabindex="-1"
        @focusout="$emit('focusout')"
        @blur.capture="$emit('blur')"
        @focus.capture="$emit('focus')"
    >
        <div @click="$emit('click')" class='dropdown-menu-button'>
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

defineEmits(["click","blur","focus","focusout"])
defineProps<Props>()

</script>

<style lang="scss">

</style>