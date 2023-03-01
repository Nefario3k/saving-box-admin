<template>
  <div>
    <v-tooltip :nudge-bottom="15" top color="#fff">
      <template v-slot:activator="{ on, attrs }">
        <div
          :style="`height: ${chartData.height}%`"
          class="chart__area-colorBar"
          v-bind="attrs"
          v-on="on"
        ></div>
        <span>{{ chartData.day }}</span>
      </template>
      <span class="tooltip__span">500</span>
    </v-tooltip>
  </div>
</template>

<script>
export default {
  props: ["chartData"],
};
</script>

<style lang="scss" scoped>
</style>