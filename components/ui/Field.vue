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

</style>