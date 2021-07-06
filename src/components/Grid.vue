<template>
  <div v-if="info.tapped" class="text-xs bg-red-200">
    {{ info.name }}
  </div>
  <div v-else class="text-xs bg-gray-100">
    {{ info.name }}
  </div>
</template>

<script>
export default {
  props: {
    info: {
      type: Object,
    },
  },
  mounted() {
    ;
  },
  unmounted() {
    ;
  },
};
</script>
