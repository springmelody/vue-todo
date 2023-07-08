<template>
  <div class="p-10 text-gray-100 mx-auto max-w-screen-lg">
    <my-dialog v-model:show="modalShow">Warning! Too much to do!</my-dialog>
    <div class="flex xl:container mx-auto flex-col pb-10">
      <note-form class="form border-lime-500" @add-note="add" />
      <note-list :notes="notes" @remove="removeNote" @check="toggleCheck" />
    </div>
  </div>
</template>

<script>
import NoteForm from "@/components/NoteForm.vue";
import NoteList from "@/components/NoteList.vue";
export default {
  name: "App",
  components: {
    NoteForm,
    NoteList,
  },
  data() {
    return {
      notes: [],
      modalShow: false,
      maxNotes: 8,
    };
  },
  created() {
    const notesList = localStorage.getItem("notes-list");

    if (notesList) {
      this.notes = JSON.parse(notesList);
    }
  },
  computed: {
    completedList() {
      return [...this.notes].filter((el) => el.completed === true);
    },
  },

  mounted() {
    this.modalShow = false;
  },

  methods: {
    mlog(id) {
      console.log("app id", id);
    },
    add(note) {
      if (note.text && this.notes.length < this.maxNotes) {
        this.notes = [...this.notes, note];
      }

      if (this.notes.length === this.maxNotes) {
        this.modalShow = true;
      }
    },
    removeNote(uniqId) {
      this.notes = this.notes.filter(({ id }) => id !== uniqId);
    },
    toggleCheck(uniqId) {
      const note = this.notes.find((el) => el.id === uniqId);
      note.completed = !note.completed;
    },
  },
  watch: {
    notes: {
      handler() {
        localStorage.setItem("notes-list", JSON.stringify(this.notes));
      },
      deep: true,
    },
  },
};
</script>

<style></style>
