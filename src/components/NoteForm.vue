<template>
  <form class="flex justify-between mb-10">
    <my-input type="text" v-model="note.text" placeholder="Enter text..." />
    <my-button class="bg-sky-400 ml-10" @click.prevent="add"
      >Add note</my-button
    >
  </form>
</template>
<script>
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
        id: crypto.randomUUID(),
        text: this.note.text,
        completed: false,
      };

      this.$emit("add-note", currentNote);
      this.note.text = "";
    },
  },
};
</script>
