<template>
  <form class="addcard" @submit.prevent="addTextToList">
    <input
      v-model="text"
      type="text"
      class="text-input"
      placeholder="Add new text"
    />
    <button type="submit" class="add-button">Add</button>
  </form>
</template>

<script>
export default {
  props: {
    listIndex: {
      type: Number,
      required: true,
    },
  },
  data: function () {
    return {
      text: "",
    };
  },
  methods: {
    addTextToList: function () {
      this.$store.dispatch("addTextToList", {
        text: this.text,
        listIndex: this.listIndex,
      });
      this.text = "";
    },
  },
};
</script>
