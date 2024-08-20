<template>
    <div>
        Hello!
    </div>
    <ChildComp :value="valueList">
        <template v-for="(_, name) in $slots" :key="name" v-slot:[name]="slotProps">
            hello!
            <button @click="onclick($slots)">Hello</button>
            <slot :name="name" v-bind="slotProps || {}">
            </slot>
        </template>
    </ChildComp>
</template>

<script setup lang="ts" generic="T">
import type { TExample } from './example.type';
import ChildComp from './ChildComp.vue';

defineProps<{
    valueList: TExample<T>;
}>();

function onclick(slots: Readonly<any>) {
    console.log(slots);
}
</script>