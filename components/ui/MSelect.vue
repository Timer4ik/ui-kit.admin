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
.control__field {
    font-family: inherit;
    display: block;
    width: 100%;
    padding: 0.75rem 1.25rem;
    font-size: 1rem;
    font-weight: 400;
    line-height: 1.3;
    color: #16192C;
    background-color: #FFF;
    background-clip: padding-box;
    border: 1px solid #E7EAF0;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    border-radius: 0.375rem;
    box-shadow: 0px 1px 2px rgba(50, 50, 71, 0.08);
    transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;


    &:focus {
        color: #16192C;
        background-color: #FFF;
        border-color: #5C60F5;
        outline: 0;
        box-shadow: 0px 1px 2px rgba(50, 50, 71, 0.08), 0 0 0 3px rgba(92, 96, 245, 0.25);
    }

    &__nomodify {
        font-size: 0.75rem !important;
        color: rgb(107, 123, 147);
    }

}

.control__select {
    &.select__active {
        color: #16192C;
        background-color: #FFF;
        border-color: #5C60F5;
        outline: 0;
        box-shadow: 0px 1px 2px rgba(50, 50, 71, 0.08), 0 0 0 3px rgba(92, 96, 245, 0.25);
    }

    .options__item.selected {
        background-color: rgb(237, 237, 237);
    }

    .options__item:hover {
        background-color: rgb(250, 250, 250);
    }

    .options__item.selected:hover {
        background-color: rgb(237, 237, 237);
    }


    .select__options {
        z-index: 1000000;
        position: absolute;
        width: 100%;
        top: 108%;
        left: 0;
        background-color: #FFF;
        border-radius: 0.375rem;
        border: 1px solid #E7EAF0;
        box-shadow: 0px 1px 2px rgba(50, 50, 71, 0.08);
        max-height: 400px;
        overflow: auto;

        // border-top-left-radius: 0;
        // border-top-right-radius: 0;
        div {
            display: block;
            width: 100%;
            padding: 0.75rem 3.75rem 0.75rem 1.25rem;
            -moz-padding-start: calc(1.25rem - 3px);
            font-size: 1rem;
            font-weight: 400;
            line-height: 1.3;
            color: #16192C;
            background-repeat: no-repeat;
            background-position: right 1.25rem center;
            background-size: 16px 12px;
            border-bottom: 1px solid #E7EAF0;
            transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
            -webkit-appearance: none;
            -moz-appearance: none;
            appearance: none;
        }

        // &__option:first-child {
        //     border: none;
        // }
    }
}
</style>
