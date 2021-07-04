<template>
    <h1>{{ title }}</h1>
    <p>{{ rows }} x {{ cols }} in {{ total }} grids</p>
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
        console.log('grids mounted');
    },
    unmounted() {
        console.log('grids unmounted()');
    },
    setup(props) {
        const total = props.rows * props.cols;
        return {
            total,
        };
    },
};
</script>
