<template>
    <Datepicker
        class="control__datepicker"
        :format="(date: Date) => `${date?.getDate()}/${date?.getMonth() + 1}/${date?.getFullYear()}`"
        v-model="date"
    />
</template>
  
<script setup lang="ts">
import { ref } from 'vue';
import Datepicker from '@vuepic/vue-datepicker';
import '@vuepic/vue-datepicker/dist/main.css';

const props = defineProps<{
    value?: Date
    label?: string
}>()

const emits = defineEmits(["change"])

const date = ref(props.value);


watch(() => date.value, () => {
    emits('change', date.value)
})
</script>
  
<style lang="scss">
.dp__input:focus {
    color: #16192C;
    background-color: #FFF;
    border-color: #5C60F5;
    outline: 0;
    box-shadow: 0px 1px 2px rgba(50, 50, 71, 0.08), 0 0 0 3px rgba(92, 96, 245, 0.25);
}

.dp__input {
    font-family: inherit;
    display: block;
    width: 100%;
    padding: 0.75rem 2.25rem;
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
}


</style>