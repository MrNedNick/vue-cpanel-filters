<template>
  <v-list-item>
    <v-radio-group v-model="title">
      <v-radio
        class="radio"
        v-for="btn in items"
        :key="btn.id"
        :label="btn.label"
        :value="btn.value"
        @click.prevent="updateTitle"
      />
    </v-radio-group>
  </v-list-item>
</template>

<script>
export default {
  props: ["title", "items"],
  methods: {
    updateTitle() {
      let newTitle = this.title;
      this.$emit("update-title", newTitle);
    },
  },
};
</script>

<style>
</style>