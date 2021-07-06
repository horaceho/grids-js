<template>
  <div class="mt-2 mb-4 p-6 max-w-sm mx-auto bg-white rounded-xl shadow-md flex items-center space-x-4">
    <div class="flex-shrink-0" @click="state.count++">
      <img class="h-12 w-12" src="../assets/logo.png" width="32" height="32" alt="horaceho.com" />
    </div>
    <div>
      <div class="text-xl font-medium text-black">{{ msg }}</div>
      <p class="text-gray-500">
        Like the icon? Click it to add {{ state.count }} ...
      </p>
    </div>
  </div>
</template>

<script>
import { reactive } from "vue";

export default {
  props: {
    msg: String,
  },
  mounted() {
    console.log("hello mounted()");
  },
  unmounted() {
    console.log("hello unmounted()");
  },
  setup(props) {
    const state = reactive({ count: 0 });
    return {
      state,
    };
  },
};
</script>
