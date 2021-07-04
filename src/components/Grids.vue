<template>
  <div class="mt-2 mb-4 p-6 max-w-sm mx-auto bg-white rounded-xl shadow-md flex items-center space-x-4">
    <div>
      <div class="text-xl font-medium text-black">{{ title }}</div>
      <p class="text-gray-500">{{ rows }} x {{ cols }} in {{ total }} grids</p>
    </div>
  </div>
</template>

<script>
import { ref, reactive } from "vue";

export default {
  props: {
    title: String,
    rows: {
      type: Number,
      default: 10,
    },
    cols: {
      type: Number,
      default: 9,
    },
  },
  mounted() {
    console.log("grids mounted");
  },
  unmounted() {
    console.log("grids unmounted()");
  },
  setup(props) {
    const total = props.rows * props.cols;
    return {
      total,
    };
  },
};
</script>
