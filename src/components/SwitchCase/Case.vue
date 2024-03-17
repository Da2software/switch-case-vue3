<script setup lang="ts">
import { ref, inject, watch, onMounted } from 'vue';

const props = defineProps({
    // take the value to compare with the parent value (caseValue)
    value: {
        required: false
    },
    defaultCase: {
        type: Boolean,
        default: false
    }
});
// take the 'caseValue' value from Switch component which is shared with the provider mechanic
const { caseValue, gotMatch, cases }: any = inject('shareProps'); // injector is the magic mechanic to get the parent property
// in case the value matches we will display the content with a 'v-if'
const isActive = ref(false);

onMounted(() => {
    if (cases.includes(props.value)) {
        throw new TypeError("Duplicated case on Switch component");
    }
    cases.push(props.value);
});

watch(caseValue, (newVal, oldVal) => {
    if (props.defaultCase) return false;
    const res = props.value === newVal;
    isActive.value = res;
    if (!gotMatch.value) {
        gotMatch.value = true;
    }
});
</script>

<template>
    <!-- Here we show or hide the slot content -->
    <template v-if="isActive || (defaultCase && !gotMatch)">
        <!-- Here we can render the content inside the Case component -->
        <slot></slot>
    </template>
</template>
