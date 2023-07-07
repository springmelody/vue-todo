<template>
  <input
    class="w-10/12 pl-5 bg-slate-800"
    type="text"
    :value="modelValue"
    @input="updateInput"
  />
</template>
<script>
export default {
  name: "my-input",
  props: {
    modelValue: [String, Number],
  },
  methods: {
    updateInput(event) {
      this.$emit("update:modelValue", event.target.value);
    },
  },
};
</script>
