<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  data: Object,
});

const onClick = () => {
  console.log(props.data.id);
};
</script>

<template>
  <div :data="props.data" class="card" @click="onClick">{{ props.data.name }}</div>
</template>
