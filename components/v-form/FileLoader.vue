<template>
    <UiControl
        :label="label"
        :invalid="!!errorMessage"
        :message="errorMessage || message"
    >
        <UiFileLoader v-model="value" />
    </UiControl>
</template>

<script setup lang="ts">
import { useField } from 'vee-validate';

interface Props {
    name: string,
    defaultValue?: any,
    rules?: any
    message?: string
    label?: string
    placeholder?: string
}

const props = defineProps<Props>()

const { value, errorMessage, resetField } = useField<any>(props.name, props.rules);

resetField({
    value: props.defaultValue, // ✅
});

</script>