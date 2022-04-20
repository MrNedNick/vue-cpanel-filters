<template>
  <div class="menu-container ml-6">
    <v-menu :close-on-content-click="false" class="menu" ref="menu" offset-y>
      <template v-slot:activator="{ on, attrs }">
        <v-btn v-bind="attrs" v-on="on" class="main-btn">
          Volume:
          {{
            data.title !== "custom"
              ? data.title
              : `${data.from} - ${data.to}`
          }}
          <v-icon>mdi-chevron-down</v-icon>
        </v-btn>
      </template>
      <v-list class="menu">
        <radio-select
          :items="volumeRadioBtns"
          :title="data.title"
          @update-title="update"
        />
        <custom-section :title="data.title" :range="data" />
        <div class="bottom">
          <apply-btn :title="data.title" @close="$refs.menu.save()" />
        </div>
      </v-list>
    </v-menu>
  </div>
</template>

<script>
import RadioSelect from "../Shared/RadioSelect.vue";
import CustomSection from "../Shared/CustomSection.vue";
import ApplyBtn from "../Shared/ApplyBtn.vue";
export default {
  props: ["data"],
  components: {
    RadioSelect,
    CustomSection,
    ApplyBtn,
  },
  methods: {
    update(title) {
      this.data.title = title;
    },
  },
  data() {
    return {
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
        {
          id: 5,
          label: "Custom",
          value: "custom",
        },
      ],
    };
  },
  computed: {
    title() {
      return this.volumeTitle;
    },
  },
  watch: {
    title(newValue, oldValue) {
      this.$emit("updateParent", this.volumeTitle);
    },
  },
};
</script>
