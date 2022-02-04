<template>
    <main class="listOfCharacters">
        <Filter />
        <ul class="listOfCharacters__list">
          <li
          v-for="character in apiData"
          :key="character.id"
          class="list__item">
            <CharacterCard
              :characterImage="character.image"
              :characterName="character.name"
              :characterStatus="character.status"
              :characterSpecies="character.species"
              :characterLocation="character.location"
              :characterEpisode="character.episode[0]"
              />
          </li>
        </ul>
    </main>

</template>

<script lang='ts'>
import axios from 'axios';
import { defineComponent, ref } from 'vue';
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
    const currentData = ref([]);
    let apiPage = 1;

    const getCharacters = async (page: number) => {
      try {
        const thisPage = page;
        const { data } = await axios({
          method: 'GET',
          url: `https://rickandmortyapi.com/api/character/?page=${thisPage}`
        });
        currentData.value = await data.results;
        apiData.value = [...apiData.value, ...currentData.value];
        console.log(apiData);
      } catch (error) {
        console.log(error);
      }
    };
    getCharacters(apiPage);

    const handleScroll = () => {
      if (
        window.scrollY + window.innerHeight >= document.body.scrollHeight - 60
      ) {
        apiPage += 1;
        getCharacters(apiPage);
      }
    };

    window.addEventListener('scroll', () => handleScroll());

    return {
      apiData
    };
  }
});
</script>

<style scoped lang='scss'>
.listOfCharacters {
  width: 100%;
  background-color: rgb(36, 40, 47);
}
ul {
  list-style-type: none;
  padding-inline-start: 0;
  display: flex;
  flex-wrap: wrap;
  column-count: 3;
  justify-content: center;
}
li {
  width: 30%;
}
</style>
