<script setup>
import { ref } from 'vue';
import DataPanel from './components/DataPanel.vue';

const leftData = ref([
  {
    id: 1,
    name: 'Shoes 1',
  },
  {
    id: 2,
    name: 'Shoes 2',
  },
  {
    id: 3,
    name: 'Shoes 3',
  },
  {
    id: 4,
    name: 'Shoes 4',
  },
  {
    id: 5,
    name: 'T-shirt 1',
  },
  {
    id: 6,
    name: 'T-shirt 2',
  },
  {
    id: 7,
    name: 'T-shirt 3',
  },
  {
    id: 8,
    name: 'T-shirt 4',
  },
]);
const rightData = ref([
  {
    id: 11,
    name: 'Jacket 1',
  },
  {
    id: 12,
    name: 'Jacket 2',
  },
  {
    id: 13,
    name: 'Jacket 3',
  },
  {
    id: 14,
    name: 'Jacket 4',
  },
  {
    id: 15,
    name: 'Hoodie 1',
  },
  {
    id: 16,
    name: 'Hoodie 2',
  },
  {
    id: 17,
    name: 'Hoodie 3',
  },
  {
    id: 18,
    name: 'Hoodie 4',
  },
]);

const onLeftSelect = (event) => {
  const cardData = leftData.value.find((item) => item.id === event.id);
  const index = leftData.value.findIndex((item) => item.id === event.id);
  const selectedCards = leftData.value.filter((item) => item.selected);
  if (!event.selected || (event.selected && selectedCards.length < 6)) {
    cardData.selected = event.selected;
  }

  leftData.value[index] = cardData;
};
const onRightSelect = (event) => {
  const index = rightData.value.findIndex((item) => item.id === event.id);
  if (event.selected) {
    rightData.value.forEach((item) => {
      item.selected = false;
    });
    rightData.value[index].selected = true;
  }
};
</script>

<template>
  <div class="container">
    <div class="panel-wrapper">
      <div class="panel">
        <data-panel :data="leftData" @select="onLeftSelect" />
      </div>
    </div>
    <div class="panel-wrapper">
      <div class="panel">
        <data-panel :data="rightData" @select="onRightSelect" />
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
  margin-top: 60px;
}
.container {
  display: flex;
  justify-content: space-around;
}
.panel-wrapper {
  width: 45%;
}
.panel {
  width: 100%;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  border: 1px solid black;
  padding: 10px;
  padding-bottom: 0;
}
</style>
