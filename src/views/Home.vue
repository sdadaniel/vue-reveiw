<template>
  <div class="home">
    {{ contentHeight }}
    <p
      class="title"
      v-for="item in items"
      :key="item.id"
      @click="openDetail(item)"
    >
      {{ item.name }}
    </p>
  </div>
</template>

<script>
import itemData from "@/mixins/itemData";
export default {
  name: "Home",
  mixins: [itemData],
  data() {
    return { contentHeight: null };
  },

  mounted() {
    console.log("Mounted");
    this.contentHeight = document.documentElement.scrollHeight;
    window.parent.postMessage({ height: this.contentHeight }, "*");
  },
  methods: {
    openDetail(item) {
      window.parent.postMessage({ detailId: item.id }, "*");
    },
  },
};
</script>

<style lang="scss" scoped>
.home {
  width: 100%;
  height: 300px;

  .title {
    padding: 50px 0px;
    background: #eee;
    box-shadow: #333;
  }
}
</style>
