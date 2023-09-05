<template>
    <UiControl
        :invalid="!!errorMessage"
        :message="errorMessage || message"
    >
        <UiCheckbox
            v-model="value"
            :label="label"
        />
    </UiControl>
</template>
<script setup lang="ts">
import { useField } from 'vee-validate';

interface Props {
    name: string,
    defaultValue?: boolean,
    rules?: any
    message?: string
    label?: string
    placeholder?: string
}

const props = defineProps<Props>()

const { value, errorMessage, resetField } = useField<boolean>(props.name, props.rules);

resetField({
    value: props?.defaultValue || false, // ✅
});

</script>