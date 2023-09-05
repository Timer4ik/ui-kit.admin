<template>
    <UiControl
        :label="label"
        :invalid="!!errorMessage"
        :message="errorMessage || message"
        :rightIcon="rightIcon"
    >

        <UiField
            v-model="value"
            :placeholder="placeholder"
        />
    </UiControl>
</template>
<script setup lang="ts">


import { useField } from 'vee-validate';

interface Props {
    rightIcon?: any
    name: string,
    defaultValue?: string,
    rules?: any
    message?: string
    label?: string
    placeholder?: string
}

const props = defineProps<Props>()

const { value, errorMessage, resetField } = useField<string>(props.name, props.rules);

resetField({
    value: props.defaultValue || "", // ✅
});

</script>