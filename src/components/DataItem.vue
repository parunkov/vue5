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
  <div :data="props.data" class="card" @click="onClick" :class="{ selected: props.data.selected }">
    {{ props.data.name }}
  </div>
</template>

<style lang="scss" scoped>
.card {
  padding: 5px;
  border: 1px solid black;
  margin-bottom: 5px;
  &.selected {
    background: black;
    color: white;
  }
}
</style>
