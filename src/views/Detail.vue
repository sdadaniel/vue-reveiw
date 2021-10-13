<template lang="">
  <div class="detail" @click="close()">
    <div class="box" @click.stop="test()">
      <div class="close" @click="close()">X</div>
      <p>{{ items.find((elem) => elem.id == $route.params.id).name }}</p>
    </div>
  </div>
</template>
<script>
import itemData from "@/mixins/itemData";
export default {
  mixins: [itemData],
  data() {
    return {};
  },
  methods: {
    close() {
      window.parent.postMessage({ close: true }, "*");
    },
    test() {
      console.log("test");
    },
  },
};
</script>
<style lang="scss">
.detail {
  position: fixed;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100vh;
  z-index: 10;

  .box {
    width: 500px;
    height: 500px;
    background: #fff;
    position: relative;

    p {
      font-size: 30px;
    }
    .close {
      width: 100px;
      height: 100px;
      background: #eee;
      position: absolute;
      top: 0px;
      right: 0px;
    }
  }
}
</style>
