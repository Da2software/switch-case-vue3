<script setup lang="ts">
import { provide, ref, watch, } from "vue";

// this is equivalent to switch(caseValue){...
const caseValue = defineModel('caseValue');
const gotMatch = ref(false);
// To avoid duplicate cases we need to identify each one.
let cases: Array<any> = [];

/* this is used on parent components to share values to descendant children components */
provide('shareProps', { caseValue, gotMatch, cases });

// reset gotMatch value if caseValue change
watch(caseValue, (newVal, oldVal) => {
    gotMatch.value = false;
    cases = [];
});
</script>
<template>
    <!-- Here we let the Switch component use the Case components as children. -->
    <slot></slot>
</template>