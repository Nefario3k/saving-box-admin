<template>
  <v-card :color="card.color" flat class="cards">
    <div>
      <p>{{ card.title }}</p>
      <div class="cards__info">
        <span class="cards__info-value">{{ card.value }}</span>
        <span class="cards__info-details">{{ card.details }}</span>
      </div>
    </div>
  </v-card>
</template>

<script>
export default {
  props: ["card"],
};
</script>

<style lang="scss" scoped>
</style>