<template>
    <article class="characterCard">
        <div class="characterCard__image">
            <img :src="theCharacterImage" alt="Image of the character" class="image__image">
        </div>
        <div class="character__data">
          <h2 class="data__character">{{name}}</h2>
          <p class="character__basics">
            <i :class="status" class="fas fa-circle"></i>
            {{status}} - {{species}}
            </p>
          <h4 class="data_info">Last known location</h4>
          <h3 class="info_item">{{location.name}}</h3>
          <h4 class="data_info">First seen in:</h4>
          <h3 class="info_item">{{episode}}</h3>
        </div>
    </article>

</template>

<script lang='ts'>
import axios from 'axios';
import { defineComponent, ref, onMounted } from 'vue';

export default defineComponent({
  name: 'CharacterCard',
  props: ['characterImage', 'characterName', 'characterStatus', 'characterSpecies', 'characterLocation', 'characterEpisode'],
  setup(props) {
    const theCharacterImage = ref(props.characterImage);
    const name = ref(props.characterName);
    const status = ref(props.characterStatus);
    const species = ref(props.characterSpecies);
    const location = ref(props.characterLocation);
    const episode = ref(props.characterEpisode);

    onMounted(async () => {
      try {
        const { data } = await axios({
          method: 'GET',
          url: episode.value
        });
        episode.value = await data.name;
      } catch (error) {
        console.log(error);
      }
    });

    return {
      theCharacterImage,
      name,
      status,
      species,
      location,
      episode
    };
  }
});
</script>

<style scoped lang='scss'>
.characterCard {
  display: flex;
  align-items: center;
  border-radius: 1rem;
  color: white;
  background-color: rgb(60, 62, 68);
  margin: 1rem;
  min-width: 100%;
  height: 18vh;
}
.characterCard__image {
  width: 25%;
}
.image__image {
  width: 100%;
  border-radius: 1rem 0 0 1rem;
}
.character__data {
  width: 75%;
}
h2, h4 {
  margin: 0.2rem 0.2rem 0.2rem 0.4rem;
}

h3, p {
  margin: 0.4rem;
}
h4 {
  color: lightgray;
}
h2 {
  font-size: 1.4rem;
}
h3 {
  font-size: 1rem;
}
h4, p, .Dead, .Alive, .unknown{
  font-size: 0.65rem;
}
.Dead {
  color:red;
}
.Alive {
  color:rgb(23, 211, 23);
}
.unknown {
  color: grey;
}

@media (min-width: 1200px) {
  .characterCard {
    min-width: 30%;
    height: auto;
}
.characterCard__image {
  width: 40%;
}
.image__image {
  width: 100%;
  border-radius: 1rem 0 0 1rem;
}

}
</style>
