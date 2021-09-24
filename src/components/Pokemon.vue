<template>
    <div @click="Details">
        <div class="card m-2">
            <img class="card-img-top"  :src="'src/images/pokemons/'+pokemon.number+'.png'" alt="Card Image">
        </div>
    </div>
</template>

<script>
    export default {
        props:['pokemon'],
        methods: {
            Details() {
                this.$router.push({
                    name: 'pokemon-detail',
                    params: { id: this.pokemon.number }
                });
            }
        }
    }
</script>

<style scoped>

    .card {
        max-height: 275px;
        max-width: 275px;
        cursor: pointer;
    }

    .card-img-top{
        margin-left: auto;
        margin-right: auto;
    }

</style>
