<template>
  <div class="container">
    <div class="row">
      <section class="characters">
        <h1 class="characters__title">Characters</h1>
        <characters-list :characters="characters"></characters-list>
      </section>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import charactersList from '@/components/CharactersList.vue';
import { urlAPI } from '@/credentials';
import getAuth from '@/utils/utils';

export default {
  components: {
    charactersList,
  },
  data() {
    return {
      characters: [],
    };
  },
  methods: {
    getCharacters() {
      const { ts, hash, publicKey } = getAuth();
      axios
        .get(
          `${urlAPI}characters?limit=50&ts=${ts}&apikey=${publicKey}&hash=${hash}`,
        )
        .then((response) => {
          this.characters = response.data.data.results;
        });
    },
  },
  mounted() {
    this.getCharacters();
  },
};
</script>
<style lang="scss">
.characters {
  padding: 40px 0;

  &__title {
    margin-bottom: 40px;
  }
}
</style>
