<template>
    <UiStack flex="same-all" gap="3">
        <label
            class="control__photoloader photoloader__block"
            :class="{ error: isInvalid }"
        >
            <input
                @change="handleOnFileChange"
                v-bind="$attrs"
                class='photoloader__input'
                type="file"
            />
            <img
                class='photoloader__image'
                src="/img/icons/upload.svg"
                alt=""
            />
            <div class='photoloader__title'>Upload a file or drag and drop</div>
            <div class='photoloader__subtitle'>PNG, JPG, GIF up to 3MB</div>
        </label>
        <img
            class="photoloader__preview"
            :src="url"
            alt=""
        >
    </UiStack>
</template>
<script setup lang="ts">
import { InputHTMLAttributes } from "vue"
defineComponent({
    inheritAttrs: false
})

interface Props extends /* @vue-ignore */  InputHTMLAttributes {
    label?: string
    isInvalid?: boolean
    modelValue?: string
}

const props = defineProps<Props>()
const emits = defineEmits(["update:modelValue"])
const url = ref<any>(null)

const handleOnFileChange = (e: any) => {
    const files = e.target.files
    if (!files?.length) {
        url.value = null;
        return emits('update:modelValue', null)
    }
    const file = files[0]
    url.value = URL.createObjectURL(file)
    emits('update:modelValue', file)

}


</script>

<style lang="scss">

</style>