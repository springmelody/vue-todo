<template>
  <div>
    <div class="list">
      <transition-group name="list">
        <note-item
          v-for="note in notes"
          :key="note.id"
          :note="note"
          :notes="notes"
          :disabled="disabled"
          @remove="$emit('remove', note)"
          @check="$emit('check', note)"
        />
      </transition-group>
    </div>
  </div>
</template>

<script>
import NoteItem from "@/components/NoteItem.vue";
export default {
  name: "NoteList",
  components: {
    NoteItem,
  },
  props: {
    notes: {
      type: Array,
      required: true,
    },
    disabled: {
      type: Boolean,
    },
  },
};
</script>
<style>
.list-enter-active,
.list-leave-active {
  transition: all 0.4s ease;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}
.list-move {
  transition: transform 0.8s ease;
}
</style>
