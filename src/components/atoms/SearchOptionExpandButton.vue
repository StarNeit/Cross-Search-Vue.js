<template>
  <v-btn
    sm6
    @click="handleClick"
    class="pl-2 py-2 mx-0 btn btn--selector"
  >
    {{selectedOption}}
    <v-icon
      right
      x-large
      class="pl-5"
    >expand_more</v-icon>
  </v-btn>
</template>

<script>
export default {
  props: ['handleClick', 'selectedOption'],
};
</script>
