<script setup>
import { defineProps } from 'vue';
import DataItem from './DataItem.vue';
const props = defineProps({
  data: Array,
});
</script>
<template>
  <data-item v-for="item in props.data" :key="item.id" :data="item">{{ item.name }}</data-item>
</template>
