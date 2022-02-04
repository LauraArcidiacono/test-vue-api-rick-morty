<template>
    <section class="characterCard">
        <div class="characterCard__image">
            <img :src="characterImage" alt="Image of the character" class="image__image">
        </div>
        <h2 class="characterCard__character">{{name}}</h2>
        <p class="character__status">{{status}}</p>
        <p class="character__species">{{species}}</p>
        <h4 class="characterCard_info">Last known location</h4>
        <h3 class="info_item">{{location.name}}</h3>
        <h4 class="characterCard_info">First seen in:</h4>
        <h3 class="info_item">{{episode}}</h3>
    </section>

</template>

<script lang='ts'>
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'CharacterCard',
  props: ['characterId', 'characterName', 'characterStatus', 'characterSpecies', 'characterLocation', 'characterEpisode'],
  setup(props) {
    const characterId = ref(props.characterId);
    const name = ref(props.characterName);
    const status = ref(props.characterStatus);
    const species = ref(props.characterSpecies);
    const location = ref(props.characterLocation);
    const episode = ref(props.characterEpisode);

    const characterImage = ref(`https://rickandmortyapi.com/api/character/avatar/${characterId.value}.jpeg`);

    return {
      characterImage,
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
    border: solid 0.1rem black
}
</style>
