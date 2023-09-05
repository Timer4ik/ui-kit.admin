<template>
    <UiControl
        :label="label"
        :invalid="!!errorMessage"
        :message="errorMessage || message"
        :rightIcon="rightIcon"
    >
        <UiMSelect
            :options="options"
            v-model:selectedItems="value"
        />
    </UiControl>
</template>
<script setup lang="ts">


import { useField } from 'vee-validate';

interface Props {
    name: string
    rightIcon?: any
    defaultValues?: {
        id: number
        value: string
        item: any
    }[] | []
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
}[] | []>(props.name, props.rules);

resetField({
    value: props.defaultValues || [], // ✅
});

</script>