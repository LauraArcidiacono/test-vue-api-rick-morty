<template>
  <div>
    <Header />
    <ListOfCharacters />
    <Footer />
  </div>
</template>

<script lang='ts'>
import { defineComponent } from 'vue';
import Header from '@/components/Header.vue';
import ListOfCharacters from '@/views/ListOfCharacters.vue';
import Footer from '@/components/Footer.vue';

export default defineComponent({
  name: 'App',
  components: {
    Header,
    ListOfCharacters,
    Footer
  }

});
</script>

<style lang='scss'>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Roboto', sans-serif;
}
body {
  min-height: 100vh;
}

</style>
