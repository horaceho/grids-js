<template>
  <div class="mt-2 mb-4 p-6 max-w-lg mx-auto bg-white rounded-xl shadow-md items-center space-x-4">
    <div id="grids" class="grid grid-flow-rows grid-rows-10 grid-cols-9 gap-2">
      <div v-for="grid of grids" :key="grid.index" class="bg-gray-100 text-center">{{ grid.name }}</div>
    </div>
    <div class="mt-4">
      <div class="text-xl font-medium text-black">{{ title }}</div>
      <p class="text-gray-500">{{ total }} grids</p>
    </div>
  </div>
</template>

<script>
import { ref, reactive } from "vue";

export default {
  props: {
    title: String,
  },
  mounted() {
    console.log("grids mounted");
  },
  unmounted() {
    console.log("grids unmounted()");
  },
  setup(props) {
    const count = 30;
    const total = props.rows * props.cols;
    let grids = [];
    let moves = [];
    for (let i = 0; i < total; i++) {
      grids.push({
        index: i,
        name: i,
      });
    }
    for (let i = 0; i < count; i++) {
      moves.push({
        index: i,
        name: "ABC " + count,
      });
    }
    console.log(grids);
    return {
      total,
      grids,
    };
  },
};
</script>
