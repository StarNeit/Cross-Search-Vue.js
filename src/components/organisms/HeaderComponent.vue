<template>
  <div class="Header">
    <LogoComponent></LogoComponent>
    <TagLineComponent></TagLineComponent>
  </div>
</template>

<script>
  import LogoComponent from '../atoms/LogoComponent';
  import TagLineComponent from '../atoms/TagLineComponent';

  export default {
    components: {
      LogoComponent,
      TagLineComponent,
    },
    data() {
      return {};
    },
  };

</script>

<style scoped>
  .Header {
    display: flex;
    width: 80%;
    margin: 0 auto;
    align-items: center;
  }
  div {
    display: block;
    position: relative;
    height: 120px;
  }
</style>
