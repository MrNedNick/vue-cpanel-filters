<template>
  <v-list-item>
    <v-radio-group v-model="itemTitle">
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
  data: function () {
    return {
      itemTitle: this.title,
    };
  },
  methods: {
    updateTitle() {
      let newTitle = this.itemTitle;
      this.$emit("update-title", newTitle);
    },
  },
};
</script>

<style>
</style>