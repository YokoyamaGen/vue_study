<template>
  <form :class="classList" @submit.prevent="addTextToList">
    <input
      v-model="text"
      type="text"
      class="text-input"
      placeholder="Add new text"
      @focusin="startEditing"
      @focusout="finishEditing"
    />
    <button type="submit" class="add-button" v-if="isEditing || bodyExists">
      Add
    </button>
  </form>
</template>

<script>
export default {
  props: {
    listIndex: {
      type: Number,
      required: true,
    },
    cardIndex: {
      type: Number,
      required: true,
    },
  },
  data: function () {
    return {
      text: "",
      isEditing: false,
    };
  },
  computed: {
    classList() {
      const classList = ["addtext"];
      if (this.isEditing) {
        classList.push("active");
      }
      if (this.bodyExists) {
        classList.push("addable");
      }
      return classList;
    },
    bodyExists() {
      return this.text.length > 0;
    },
  },
  methods: {
    startEditing: function () {
      this.isEditing = true;
    },
    finishEditing: function () {
      this.isEditing = false;
    },
    addTextToList: function () {
      this.$store.dispatch("addTextToList", {
        text: this.text,
        listIndex: this.listIndex,
        cardIndex: this.cardIndex,
      });
      this.text = "";
    },
  },
};
</script>