<template>
  <div
    class="movie-item mb-5 border border-zinc-300 px-8 py-2 flex justify-between items-center gap-10"
  >
    <p>{{ text }}</p>
    <div class="flex justify-between gap-10">
      <my-button class="bg-rose-400" @click="$emit('remove')">Delete</my-button>
      <input @click="$emit('check')" type="checkbox" :checked="completed" />
    </div>
  </div>
</template>

<script>
export default {
  name: "NoteItem",
  props: {
    id: {
      type: String,
      required: true,
    },
    text: {
      type: String,
      required: true,
    },
    completed: {
      type: Boolean,
      required: true,
    },
  },
};
</script>
