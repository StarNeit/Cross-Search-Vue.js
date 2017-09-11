<template>
  <v-menu
    v-if="visibility"
    lazy
    :close-on-content-click="true"
    transition="scale-transition"
    :nudge-left="0"
    :nudge-bottom="30"
    min-width="290px"
    style="vertical-align: baseline;"
    class="px-3"
    sm6 >
    <v-date-picker v-model="selectedDate" scrollable></v-date-picker>
    <v-text-field
      slot="activator"
      v-model="selectedDate"
      placeholder="YYYY-MM-DD"
      append-icon="event"
      readonly
    ></v-text-field>
  </v-menu>
</template>

<script>
export default {
  props: ['visibility', 'selectedDate'],
};
</script>
