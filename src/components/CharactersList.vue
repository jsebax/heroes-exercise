<template>
  <div class="characters-list">
    <character-card
      v-for="character in characters"
      :key="character.id"
      :characterId="character.id"
      :name="character.name"
      :description="character.description"
      :thumbnail="`${character.thumbnail.path}.${character.thumbnail.extension}`"
    ></character-card>
  </div>
</template>

<script>
import characterCard from '@/components/CharacterCard.vue';

export default {
  components: {
    characterCard,
  },
  props: {
    characters: Array,
  },
};
</script>

<style scoped lang="scss">
.characters-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
  align-items: flex-start;
  margin-bottom: -40px;

  @include breakpoint(sm) {
    margin: 0 -20px -40px;
  }
}
</style>
