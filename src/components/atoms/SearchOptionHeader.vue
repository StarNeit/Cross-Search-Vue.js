<template>

  <v-layout
    row
    wrap
    block
    class="py-2 filter--option"
  >
    <span
      class="filter--option-title"
    >All years</span>
    <v-btn
      icon
      @click="handleClose"
      class="close-btn"
    >
      <v-icon>close</v-icon>
    </v-btn>
  </v-layout>

</template>

<style scoped lang="less">
@import '../../assets/styles/theme.less';
.filter--option{
  background-color: @background-grey;
  color: @selector-color;
  font-weight: lighter;
  .filter--option-title {
    font-weight: bold;
  }
  .close-btn {
    color: @selector-color;
    position: absolute;
    top: 8px;
    right: 0;
    margin: 0;
    height: 24px;
    width: 24px;

  }
}
</style>
<script>
export default {
  props: ['handleClose'],
};
</script>
