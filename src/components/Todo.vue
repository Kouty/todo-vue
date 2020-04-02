<template>
  <div>
    <input type="text" v-model="model.text" />
    <input type="checkbox" v-model="model.completed" />
    <input type="button" value="delete" @click="onDelete()" />
  </div>
</template>

<script>
export default {
  name: "Todo",
  props: ["model"],
  data() {
    return {
      todo: {
        text: this.text,
        completed: this.completed
      }
    };
  },
  methods: {
    onDelete() {
      this.$emit("delete");
    }
  }
};
</script>

<style>
</style>
