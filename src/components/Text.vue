<template>
  <div class="text">
    <button class="close-button" @click="removeTextFromList">×</button>
    <div class="body">
      {{ text }}
    </div>
  </div>
</template>
<script>
export default {
  props: {
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
    removeTextFromList: function () {
      if (confirm("本当にこのテキストを削除しますか？")) {
        this.$store.dispatch("removeTextFromList", {
          cardIndex: this.cardIndex,
          listIndex: this.listIndex,
        });
      }
    },
  },
};
</script>
