<template>
  <div class="menu-container">
    <v-menu offset-y :close-on-content-click="false" class="menu">
      <template v-slot:activator="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" class="main-btn">
          Volume: {{ volumeTitle }}
          <v-icon>mdi-chevron-down</v-icon>
        </v-btn>
      </template>
      <v-list class="menu">
        <v-list-item>
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
        </v-list-item>

        <v-divider />
        <div class="custom-section ml-2 mr-2">
          <v-container>
            <div class="flex">
              <div>From</div>
              <v-text-field
                outlined
                :disabled="isDisabled()"
                v-model="volumeRange.from"
                value="from"
              />
            </div>
          </v-container>
          <v-container>
            <div class="flex">
              <div>To*</div>
              <v-text-field
                outlined
                :disabled="isDisabled()"
                value="to"
                v-model="volumeRange.to"
              />
            </div>
          </v-container>
        </div>
        <div class="section-label">*Max. value is unlimited</div>
        <div class="bottom">
          <v-btn class="apply-btn" :disabled="isDisabled()"> Apply </v-btn>
        </div>
      </v-list>
    </v-menu>
  </div>
</template>

<script>
export default {
  data() {
    return {
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
  methods: {
    isDisabled() {
      return this.volumeTitle !== "custom" 

    },
  },
};
</script>

<style>
.v-list-item {
  padding: 0;
}
.radio{
  margin-top: 0px;
  padding: 8px 50px 8px 8px;
}
.radio:hover {
  background: black;
}
.v-input--radio-group--column .v-radio:not(:last-child):not(:only-child) {
    margin-bottom: 0px;
}
</style>