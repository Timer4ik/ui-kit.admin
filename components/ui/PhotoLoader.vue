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
    modelValue: string
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
.photoloader {
    &__block {
        position: relative;
        font-family: Inter, ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Helvetica Neue, Arial, Noto Sans, Liberation Sans, sans-serif, Apple Color Emoji, Segoe UI Emoji, Segoe UI Symbol, Noto Color Emoji;
        width: 100%;
        text-align: center;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        height: 250px;
        border: 2px dashed #E7EAF0;
        border-radius: 10px;
        transition: all 0.2s linear;
        cursor: pointer;
    }

    &__block.error {
        transition: all 0.2s linear;
    }

    &__label {
        margin-bottom: 0.5rem;
        font-size: 0.875rem;
        font-weight: 500;
        color: #16192C;
    }

    &__input {
        display: none;
    }

    &__image {
        z-index: 2;
        width: 30px;
        margin-bottom: 12px;

    }

    &__title {
        z-index: 2;
        font-weight: 500;
        font-size: 14px;
        color: rgb(82, 95, 127);
        margin-bottom: 12px;
    }

    &__subtitle {
        z-index: 2;
        font-size: 12px;
        color: rgb(136, 152, 169);
        margin-bottom: 12px;
    }

    &__preview {
        max-height: 250px;
    }
}
</style>