<template>
    <section class="listOfCharacters">
        <h2 class="listOfCharacters__title">Dashboard</h2>
        <CharacterCard />
    </section>

</template>

<script lang='ts'>
import { defineComponent } from 'vue';
import CharacterCard from '@/components/CharacterCard.vue';

export default defineComponent({
  name: 'ListOfCharacters',
  components: {
    CharacterCard
  }
});
</script>

<style scoped lang='scss'>

</style>
