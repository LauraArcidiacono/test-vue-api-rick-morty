<template>
    <main class="listOfCharacters">
        <Filter
          :functionGetCharacters="getCharacters"
        />
        <ul class="listOfCharacters__list">
          <li
            v-for="character in apiData"
            :key="character.id"
            class="list__item"
          >
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
    const maxPagesAvailableOnApi = 42;
    let currentKey = '';
    let currentValue = '';

    // TODO: move the logic to diferents modules and then import it here to use it
    const getCharacters = async (page: number, key = '', value = '') => {
      try {
        const thisPage = page;
        if (page === 1) {
          apiData.value = [];
        }
        if (key === '' || value === '') {
          const { data } = await axios({
            method: 'GET',
            url: `https://rickandmortyapi.com/api/character/?page=${thisPage}`
          });
          currentData.value = await data.results;
          apiData.value = [...apiData.value, ...currentData.value];
        } else {
          currentKey = key;
          currentValue = value;
          const { data } = await axios({
            method: 'GET',
            url: `https://rickandmortyapi.com/api/character/?page=${thisPage}&${key}=${value}`
          });
          currentData.value = await data.results;
          apiData.value = [...apiData.value, ...currentData.value];
        }
      } catch (error) {
        console.log(error);
      }
    };
    getCharacters(apiPage);

    // TODO optimize function handleScroll to evoit make request when there is no more
    // pages on the api, user 404 message to do it?
    const handleScroll = () => {
      if (apiPage <= maxPagesAvailableOnApi
      && window.scrollY + window.innerHeight >= document.body.scrollHeight - 60
      ) {
        apiPage += 1;
        getCharacters(apiPage, currentKey, currentValue);
      }
    };

    window.addEventListener('scroll', () => handleScroll());

    return {
      apiData,
      getCharacters
    };
  }
});
</script>

<style scoped lang='scss'>
.listOfCharacters {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  background-color: rgb(36, 40, 47);
}
ul {
  list-style-type: none;
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
}
li {
  width: 85%;
  min-width: 380px;
  margin: 0.5rem;
}

@media (min-width: 400px) {
ul {
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
}
li {
  width: 30%;
}
}
</style>
