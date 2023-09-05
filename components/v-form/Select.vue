<template>
    <UiControl
        :label="label"
        :invalid="!!errorMessage"
        :message="errorMessage || message"
        :rightIcon="rightIcon"
    >
        <UiSelect
            :options="options"
            v-model:selectedItem="value"
        />
    </UiControl>
</template>
<script setup lang="ts">


import { useField } from 'vee-validate';

interface Props {
    rightIcon?: any
    name: string
    defaultValue?: {
        id: number
        value: string
        item: any
    } | null
    rules?: any
    message?: string
    options: {
        id: number
        value: string
        item: any
    }[]
    label?: string
    placeholder?: string
}

const props = defineProps<Props>()

const { value, errorMessage, resetField } = useField<{
    id: number
    value: string
    item: any
} | null>(props.name, props.rules);

resetField({
    value: props.defaultValue || null, // ✅
});

</script>