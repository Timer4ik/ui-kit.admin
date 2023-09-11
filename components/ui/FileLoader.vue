<template>
    <label class='control__fileloader fileloader'>
        <div
            v-if="label"
            class='fileloader__label'
        >
            {{ label }}
        </div>
        <input
            @change="handleOnFileChange"

            v-bind="$attrs"
            class='fileloader__input'
            type="file"
        />
    </label>
</template>
<script setup lang="ts">
import { InputHTMLAttributes } from "vue"
defineComponent({
    inheritAttrs: false
})

interface Props extends  /* @vue-ignore */  InputHTMLAttributes {
    label?: string
    modelValue: any
}
const emits = defineEmits(["update:modelValue"])
defineProps<Props>()

const handleOnFileChange = (e: any) => {
    const files = e.target.files
    if (!files?.length) {
        return emits('update:modelValue', null)
    }
    const file = files[0]
    emits('update:modelValue', file)
}

</script>

<style lang="scss">
</style>