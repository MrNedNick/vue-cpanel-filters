<template>
  <div class="mt-10 table">
    <span class="mb-2">
      Position Filter:
      {{
        position.title === "custom"
          ? `${position.from} - ${position.to}`
          : position.title
      }}
    </span>
    <span class="mb-2">
      Volume Filter:
      {{
        volume.title === "custom"
          ? `${volume.from} - ${volume.to}`
          : volume.title
      }}
    </span>
    <span class="mb-2">
      Cpc Filter:
      {{ cpc.title === "custom" ? `${cpc.from} - ${cpc.to}` : cpc.title }}
    </span>
    <span class="mb-2">
      Competitor Filter:
      {{
        competitor.title === "custom"
          ? `${competitor.from} - ${competitor.to}`
          : competitor.title
      }}
    </span>
    <span class="mb-2">
      Groupings Filter:
      {{ `${groupings.firstSelect} - ${groupings.secondSelect}` }}
    </span>
    <!-- <span class="mb-2"> Advanced Filter: {{ advanced }}</span> -->
    <span class="mb-2"> Word Count Filter: {{ word }}</span>
  </div>
</template>

<script>
export default {
  props: ["position", "volume", "cpc", "competitor", "groupings", "advanced", "word"],
};
</script>

<style>
</style>