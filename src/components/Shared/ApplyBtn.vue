<template>
    <v-btn
      :disabled="isDisabled()"
      class="apply-btn mt-4 mb-4"
      @click="closeMenu"
    > 
      Apply 
    </v-btn>
</template>

<script>
export default {
  props: ["title"],
  methods: {
    isDisabled() {
      return this.title !== "custom";
    },
    closeMenu() {
      this.$emit('close')
    }
  },
};
</script>

<style lang='scss'>
.apply-btn {
  width: 169px;
  height: 40px;
  & .v-btn__content {
    color: white;
    font-family: Source Sans Pro;
    font-weight: 600;
    font-size: 14px;
    line-height: 18px;
    text-transform: none;
  }
}
.apply-btn.theme--light.v-btn.v-btn--has-bg {
  background-color: #3366ff !important;
  border-radius: 6px;
}
.apply-btn.theme--light.v-btn.v-btn--disabled.v-btn--has-bg {
  background-color: rgba(0, 0, 0, 0.12) !important;
}
.bottom {
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>