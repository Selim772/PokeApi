<template>
    <div class="header">
        <h6 class=" display-4">
            <router-link :to="{ name: 'home' }"> PokéAPI </router-link>
        </h6>
    </div>
</template>

<style scoped>

    .header {
        background-color: #e7da21;
        color: rgba(5, 40, 199, 0.801);
        text-align: center;
    }

    a {
        text-decoration: none;
        color: inherit;
    }

</style>