<template>
    <div
        class="control__field control__select"
        :class="{ select__active: isOpened }"
        @click="isOpened = !isOpened"
    >
        <div class="select__value">{{ "Выбрано " + selectedItems?.length || "Не выбрано" }}</div>

        <div
            v-if="isOpened"
            class="select__options"
        >
            <div
                class="options__item"
                v-for="option in options"
                :key="option.id"
                @click="selectedItems?.find(i => option.id == i.id) ?
                    $emit('update:selectedItems', selectedItems?.filter(i => i.id !== option.id)) :
                    $emit('update:selectedItems', [...selectedItems, option])"
                :class="{ selected: selectedItems?.find(i => option.id == i.id) }"
            >
                {{ option.value }}
            </div>
        </div>
    </div>
</template>
<script setup lang="ts">

interface Props {
    label?: string
    selectedItems: {
        id: number
        value: string,
        item: any
    }[]
    isInvalid?: boolean
    options: {
        id: number
        value: string,
        item: any
    }[]
}

interface Emits {
    (event: "update:selectedItems", items: any): void
}
const props = defineProps<Props>()
const emits = defineEmits<Emits>()

const isOpened = ref(false)

</script>

<style lang="scss">

</style>
