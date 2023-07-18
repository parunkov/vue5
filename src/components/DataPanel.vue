<script setup>
import { defineProps, defineEmits } from 'vue';
import DataItem from './DataItem.vue';

const props = defineProps({
  data: Array,
});
const emit = defineEmits(['select']);

const onSelect = (event) => {
  emit('select', { id: event.id, selected: event.selected });
};
</script>

<template>
  <data-item v-for="item in props.data" :key="item.id" :data="item" @select="onSelect">{{
    item.name
  }}</data-item>
</template>
