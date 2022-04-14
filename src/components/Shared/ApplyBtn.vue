<template>
  <v-btn
    :disabled="isDisabled()"
    class="apply-btn"
  > 
    Apply 
  </v-btn>
</template>

<script>
export default {
  props: [
    'title'
  ],
  methods: {
    isDisabled() {
      return this.title !== "custom";
    },
  },
}
</script>

<style>

</style>