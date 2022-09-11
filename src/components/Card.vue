<template>
  <div class="card">
    <button class="close-button" @click="removeCardFromList">×</button>
    <div class="body">
      {{ body }}
      <text-body :text="text" :listIndex="listIndex" :cardIndex="cardIndex" />
    </div>
    <text-add :listIndex="listIndex" :cardIndex="cardIndex" />
  </div>
</template>
<script>
import TextAdd from "./TextAdd";
import TextBody from "./Text";

export default {
  components: {
    TextAdd,
    TextBody,
  },
  props: {
    body: {
      type: String,
      required: true,
    },
    text: {
      type: String,
      required: true,
    },
    listIndex: {
      type: Number,
      required: true,
    },
    cardIndex: {
      type: Number,
      required: true,
    },
  },
  methods: {
    removeCardFromList: function () {
      if (confirm("本当にこのカードを削除しますか？")) {
        this.$store.dispatch("removeCardFromList", {
          cardIndex: this.cardIndex,
          listIndex: this.listIndex,
        });
      }
    },
  },
};
</script>