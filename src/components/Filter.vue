<template>
    <section class="filter">
        <label for="filter">Search your Character:</label>
            <input
                class="filter__imput"
                type="text"
                name="search"
                placeholder="Rick..."
                />
    </section>

</template>

<script lang='ts'>
import { defineComponent } from 'vue';

export default defineComponent({

});
</script>

<style scoped lang='scss'>
.filter {
    margin-left: 2rem;
    color: white;
}
.filter__imput {
    height: 1.5rem;
    width: 30vw;
    font-size: 1rem;
    margin: 1rem;
}
</style>
