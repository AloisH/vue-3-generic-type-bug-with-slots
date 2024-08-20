<template>
    <div>
        Bonjour
        <slot name="hello" value=""></slot>
    </div>
</template>

<script setup lang="ts" generic="T">
import { onMounted } from 'vue';

defineSlots<{
    hello?(): any;
}>();

const props = defineProps<{ value: T }>(
);


onMounted(() => {
    console.log(props.value);
})
</script>