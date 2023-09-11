
<template>
    <label class='control__checkbox checkbox'>
        <input
            v-bind="$attrs"
            class='checkbox__input'
            type="checkbox"
            :checked="modelValue"
            @input="$emit('update:modelValue', ($event?.target as HTMLInputElement).checked)"
        />
        <div
            class='checkbox__label'
            v-if="label"
        >
            {{ label }}
        </div>
    </label>
</template>
<script setup lang="ts">
import { InputHTMLAttributes } from "vue"

defineComponent({
    inheritAttrs: false
})

interface Props extends /* @vue-ignore */ InputHTMLAttributes {
    label?: string
    modelValue?: boolean
}
defineProps<Props>()

defineEmits(["update:modelValue"])

</script>

<style lang="scss">
</style>