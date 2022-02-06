<template>
    <section class="filter">
        <label for="filter">Search your Character:</label>
            <input
                class="filter__input"
                type="text"
                name="customFilter"
                placeholder="Comming soon... :-)"
                v-model.trim="inputData"
                v-on:input="customFilter(inputData)"
                />
    </section>

</template>

<script lang='ts'>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Filter',

  setup() {
    const inputData = '';

    const customFilter = (valueInput: string) => {
      const stringFromInput = valueInput.toLowerCase().replace(/[^a-z:\s]/g, '');
      const arrayKeyValue = stringFromInput.split(':');
      return arrayKeyValue;
    };

    const [key, value] = customFilter(inputData);
    console.log('key value: ', key, value);

    return {
      inputData,
      customFilter
    };
  }
});
</script>

<style scoped lang='scss'>
.filter {
    display: flex;
    flex-direction: column;
    align-content: center;
    color: white;
}
.filter__input {
    height: 1.5rem;
    width: 100%;
    font-size: 1rem;
    margin-top: 1rem;
}
label {
    width: 15rem;
    text-align: center;
    margin-top: 1rem;
}

@media (min-width:500px){
.filter {
    flex-direction: row;
    width: 70%;
}
}
</style>
