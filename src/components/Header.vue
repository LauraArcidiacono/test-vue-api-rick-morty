<template>
    <section class="header">
        <h1 class="header__title">Rick and Morty characters</h1>
        <div class="header__image">
            <img
                src="../assets/header1.webp"
                alt="Image of Rick, Morty and other characters"
                class="image__image"
            />
        </div>
    </section>
</template>

<style scoped lang='scss'>
// duplicación
.header {
    width: 100%;
}
h1 {
    display: none;
}
.header__image {
    width: 100%;
    font-size: 0;
}
.image__image {
    width: 100%;
}
</style>
