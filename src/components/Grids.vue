<template>
  <div class="mt-2 mb-4 p-6 max-w-lg mx-auto bg-white rounded-xl shadow-md items-center space-x-4">
    <div id="grids" class="grid grid-flow-rows grid-rows-10 grid-cols-9 gap-1">
      <div v-for="grid of state.grids" :key="grid.index" @click="tap(grid.index)" class="bg-gray-200 text-center">
        <div v-if="grid.tapped" class="bg-red-200">
          {{ grid.name }}
        </div>
        <div v-else class="bg-gray-200">
          {{ grid.name }}
        </div>
      </div>
    </div>
    <div class="mt-4">
      <div class="text-xl font-medium text-black">{{ title }}</div>
      <p class="text-gray-500">
        {{ total }} grids
        <span v-for="tap of state.taps">
          | {{ tap }}
        </span>
        <span v-if="state.taps.length > 0">
          [{{ state.taps.length }}]
        </span>
      </p>
    </div>
  </div>
</template>

<script>
import { ref, reactive } from "vue";

export default {
  props: {
    title: { type: String, default: "Grids" },
    rows: { type: Number, default: 10 },
    cols: { type: Number, default: 9 },
  },
  methods: {
    tap(index) {
      var at = this.state.taps.indexOf(index);
      if (at > -1) {
        this.state.taps.splice(at, 1);
      } else {
        this.state.taps.push(index);
      }
      this.state.grids[index].tapped = !this.state.grids[index].tapped;
    },
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
    const state = reactive({
      grids: [],
      taps: [],
    });
    let moves = [];
    for (let i = 0; i < total; i++) {
      state.grids.push({
        index: i,
        name: i,
        tapped: false,
      });
    }
    for (let i = 0; i < count; i++) {
      moves.push({
        index: i,
        name: "ABC " + i,
      });
    }
    return {
      total,
      state,
    };
  },
};
</script>
