<template >
    <div
        tabindex="-1"
        @focusout="isOpened = false"
    >
        <div
            @click.stop="isOpened = !isOpened"
            class="control__field control__select"
            :class="{ select__active: isOpened }"
        >
            <div class="select__value">{{ selectedItem?.value || "Не выбрано" }}</div>

            <div
                v-if="isOpened"
                class="select__options"
            >
                <div
                    class="options__item"
                    v-for="option in options"
                    :key="option.id"
                    @click.stop="selectedItem?.id === option.id ? $emit('update:selectedItem', null) : $emit('update:selectedItem', option)"
                    :class="{ selected: option?.id == selectedItem?.id }"
                >
                    {{ option?.value }}
                </div>
            </div>
        </div>
    </div>
</template>
<script setup lang="ts">

interface Props {
    label?: string
    selectedItem?: {
        id: number
        value: string,
        item: any
    } | null
    isInvalid?: boolean
    options: {
        id: number
        value: string,
        item: any
    }[]
}

interface Emits {
    (event: "update:selectedItem", items: any): void
}
const props = defineProps<Props>()
const emits = defineEmits<Emits>()

const isOpened = ref(false)

</script>

<style lang="scss"></style>
