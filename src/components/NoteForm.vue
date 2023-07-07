<template>
  <form class="flex justify-between mb-10">
    <my-input type="text" v-model="note.text" placeholder="Enter text..." />
    <my-button class="bg-sky-400 ml-10" @click.prevent="add"
      >Add note</my-button
    >
  </form>
</template>
<script>
import uniqueId from "lodash/uniqueId";
export default {
  name: "NoteForm",
  data() {
    return {
      note: {
        text: "",
      },
    };
  },
  methods: {
    add() {
      const currentNote = {
        id: uniqueId(),
        text: this.note.text,
        completed: false,
      };

      this.$emit("add-note", currentNote);
      this.note.text = "";
    },
  },
};
</script>
