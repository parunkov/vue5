<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
  data: Object,
});
const emit = defineEmits(['select']);

const onClick = () => {
  emit('select', { id: props.data.id, selected: !props.data.selected });
};
</script>

<template>
  <div :data="props.data" class="card" @click="onClick">{{ props.data.name }}</div>
</template>
