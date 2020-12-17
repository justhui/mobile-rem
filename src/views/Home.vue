<template>
  <div class="home">
    <van-uploader v-model="fileList" multiple :max-count="2" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      fileList: [],
    };
  },
};
</script>

<style lang="scss" scoped>
  .home {
    display: flex;
    justify-content: center;
    margin-top: 30vh;
  }
  
</style>