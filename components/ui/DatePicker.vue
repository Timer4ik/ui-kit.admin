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



</style>