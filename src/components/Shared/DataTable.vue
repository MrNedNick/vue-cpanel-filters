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
        <!-- <span> Volume Filter: {{ volumeFilter }}</span>
        <span> Cpc Filter: {{ cpcFilter }}</span>
        <span> AdvancedFilter: {{ advancedFilter }}</span> -->
      </div>
</template>

<script>
export default {
    props: [
        "position",
        "volume",
        "cpc",
        "competitor",
        "groupings"
    ]
}
</script>

<style>

</style>