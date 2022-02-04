<template>
    <section class="listOfCharacters">
        <h2 class="listOfCharacters__title">Dashboard</h2>
        <Filter />
        <ul class="listOfCharacters__list">
          <li
          v-for="character in apiData"
          :key="character.id"
          class="list__item">
            <CharacterCard
              :characterId="character.id"
              :characterName="character.name"
              :characterStatus="character.status"
              :characterSpecies="character.species"
              :characterLocation="character.location"
              :characterEpisode="character.episode[1]"
              />
          </li>
        </ul>
    </section>

</template>

<script lang='ts'>
import axios from 'axios';
import { defineComponent, onMounted, ref } from 'vue';
import CharacterCard from '@/components/CharacterCard.vue';
import Filter from '@/components/Filter.vue';

export default defineComponent({
  name: 'ListOfCharacters',
  components: {
    Filter,
    CharacterCard
  },

  setup() {
    const apiData = ref([]);

    onMounted(async () => {
      try {
        const { data } = await axios({
          method: 'GET',
          url: 'https://rickandmortyapi.com/api/character'
        });
        apiData.value = await data.results;
      } catch (error) {
        console.log(error);
      }
    });

    return {
      apiData
    };
  }
});
</script>

<style scoped lang='scss'>

</style>
