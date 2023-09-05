<template>
    <UiControl
        :label="label"
        :invalid="!!errorMessage"
        :message="errorMessage || message"
        :rightIcon="rightIcon"
    >
        <UiDatePicker
            :value="value"
            @change="(newDate) => setValue(newDate)"
        />
    </UiControl>
</template>

<script setup lang="ts">
import { useField } from 'vee-validate';

interface Props {
    rightIcon?: any
    name: string,
    defaultValue?: Date,
    rules?: any
    message?: string
    label?: string
    placeholder?: string
}
const props = defineProps<Props>()

const { value, errorMessage, resetField, setValue } = useField<Date>(props.name, props.rules);

resetField({
    value: props.defaultValue || new Date(), // ✅
});


</script>