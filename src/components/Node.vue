<template>
  <g
    v-if="node.x !== undefined"
  >
    <circle :r="medianQuantidadeVagas" :fill="color(node.areas)"></circle>
    <text
      text-anchor="middle"
      font-family="Verdana"
      alignment-baseline="central"
      font-size="10"
    >
      {{ node.sigla }}
    </text>
  </g>
</template>

<script>
export default {
  name: 'Node',
  props: {
    node: {
      type: Object,
      default() {
        return undefined;
      },
    },
    color: {
      type: Function,
      default() {
        return undefined;
      },
    },
  },
  computed: {

  },
  methods: {
    median(values) {
      if (values.length === 0) return 0;

      values.sort((a, b) => a - b);

      const half = Math.floor(values.length / 2);

      if (values.length % 2) return values[half];

      return (values[half - 1] + values[half]) / 2.0;
    },
  },
};
</script>
