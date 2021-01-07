<template>
  <div class="list">
    <div class="listheader">
      <p class="list-title">{{ title }}</p>
      <div class="deletelist" @click="removeList">×</div>
    </div>
    <!-- ★ここに追記 -->
    <card-add :listIndex="listIndex" />
  </div>
</template>

<script>
// ★追記
import CardAdd from "./CardAdd";

export default {
  // ★ここから追記
  components: {
    CardAdd,
  },
  // ★ここまで追記
  props: {
    title: {
      type: String,
      required: true,
    },
    listIndex: {
      type: Number,
      required: true,
    },
  },
  methods: {
    removeList: function() {
      if (confirm("本当にこのリストを削除しますか？")) {
        this.$store.dispatch("removelist", { listIndex: this.listIndex });
      }
    },
  },
};
</script>
