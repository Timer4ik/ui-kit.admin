<template>
    <input
        class="control__field"
        :class="invalid"
        @input="
            $emit('update:modelValue', ($event.target as HTMLInputElement).value)
            "
        :value="modelValue"
    />
</template>
  
<script setup lang="ts">


import { InputHTMLAttributes } from "nuxt/dist/app/compat/capi";

interface Props extends /* @vue-ignore */ InputHTMLAttributes {
    modelValue?: string;
    invalid?: boolean;
}

interface Emits {
    (event: "update:modelValue"): void;
}

defineEmits<Emits>();
defineProps<Props>();
</script>

<style lang="scss">
.control__field {
    font-family: inherit;
    display: block;
    width: 100%;
    padding: 0.75rem 1.25rem;
    font-size: 1rem;
    font-weight: 400;
    line-height: 1.3;
    color: #16192C;
    background-color: #FFF;
    background-clip: padding-box;
    border: 1px solid #E7EAF0;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    border-radius: 0.375rem;
    box-shadow: 0px 1px 2px rgba(50, 50, 71, 0.08);
    transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;


    &:focus {
        color: #16192C;
        background-color: #FFF;
        border-color: #5C60F5;
        outline: 0;
        box-shadow: 0px 1px 2px rgba(50, 50, 71, 0.08), 0 0 0 3px rgba(92, 96, 245, 0.25);
    }

    &__nomodify {
        font-size: 0.75rem !important;
        color: rgb(107, 123, 147);
    }
}
</style>