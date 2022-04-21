
<template>
  <div class="menu-container">
    <v-menu :close-on-content-click="false" class="menu" ref="menu" offset-y>
      <template v-slot:activator="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" class="main-btn">
          Pos:

          <v-icon>mdi-chevron-down</v-icon>
        </v-btn>
      </template>
      <v-list class="menu">
        <radio-select
          :items="positionRadioBtnsTop"
          :title="positionTitle"
          @update-title="update"
        />
        <v-divider />
        <radio-select
          :items="positionRadioBtns"
          :title="positionTitle"
          @update-title="update"
        />
        <custom-section :range="positionRange" :title="positionTitle" />
        <div class="bottom">
          <apply-btn :title="positionTitle" @close="$refs.menu.save()" />
        </div>
      </v-list>
    </v-menu>
  </div>
</template>
  <!-- <div class="menu-container">
    <div class="select-wrapper">
      <v-select
        class="select"
        :items="items"
        clearable
        offset-y
        outlined
        append-icon="mdi-chevron-down"
        color="#033"
        background-color="white"
        deletable-chips
        :menu-props="{
          top: false,
          offsetY: true,
          maxHeight: 700,
          maxWidth: 200,
        }"
      >
        <template v-slot:prepend-inner class="input-title"> Volume: </template>
        <template v-slot:append-item>
          <v-radio-group v-model="volumeTitle">
            <v-radio
              class="radio"
              v-for="btn in volumeRadioBtns"
              :key="btn.id"
              :label="btn.label"
              :value="btn.value"
            />
            <v-radio class="radio" label="Custom" value="custom" />
          </v-radio-group>
          <v-divider />
          <div class="custom-section ml-2 mr-2">
            <v-container>
              <div class="flex">
                <div>From</div>
                <v-text-field outlined value="from" />
              </div>
            </v-container>
            <div class="custom-line">-</div>
            <v-container>
              <div class="flex">
                <div>To*</div>
                <v-text-field outlined value="to" />
              </div>
            </v-container>
          </div>
          <div class="section-label">*Max. value is unlimited</div>
          <div class="bottom">
            <v-btn class="apply-btn"> Apply </v-btn>
          </div>
        </template>
      </v-select>
    </div>
  </div> -->

</template>

<script>
export default {
  data() {
    return {
      items: ["Foo", "Bar", "Fizz", "Buzz"],
      disabled: false,
      volumeTitle: "0-10",
      volumeRange: [{ from: "0" }, { to: "0" }],
      volumeRadioBtns: [
        {
          id: 1,
          label: "0-10",
          value: "0-10",
        },
        {
          id: 2,
          label: "11-100",
          value: "11-100",
        },
        {
          id: 3,
          label: "101-1000",
          value: "101-1000",
        },
        {
          id: 4,
          label: "1001-5000",
          value: "1001-5000",
        },
      ],
    };
  },
};
</script>

<style>
</style>