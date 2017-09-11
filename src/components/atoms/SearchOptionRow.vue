<template>
  <v-layout
    row
    wrap
    block
    class="filter--option"
  >
    <v-flex
      xs4
      class="py-2"
      v-for="(item, index) in data"
      :key="index"
      @click="setOption(item)"
    >{{item}}</v-flex>
  </v-layout>
</template>

<script>
export default {
  props: ['data', 'setOption'],
};
</script>
