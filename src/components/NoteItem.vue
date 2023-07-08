<template>
  <div
    class="movie-item mb-5 border border-zinc-300 px-8 py-2 flex justify-between items-center gap-10"
  >
    <p>{{ note.text }}</p>
    <div class="flex justify-between gap-10">
      <my-button class="bg-rose-400" @click="$emit('remove', note)"
        >Delete</my-button
      >
      <input
        @click="$emit('check', note)"
        v-model="completed"
        type="checkbox"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "NoteItem",
  props: {
    note: {
      type: Object,
    },
  },
};
</script>
