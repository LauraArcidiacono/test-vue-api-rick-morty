<template>
  <section class="filter">
    <label for="filter">Search your Character: </label>
    <input
      id="filter"
      class="filter__input"
      type="text"
      name="search"
      placeholder="Comming soon... :-)"
    />
  </section>
</template>

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

@media (min-width: 500px) {
  .filter {
    flex-direction: row;
    width: 70%;
  }
}
</style>
