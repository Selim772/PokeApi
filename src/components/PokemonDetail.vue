<template>
        <div class="col-12">
            <app-loading-panel v-if="this.currentStatus === status.LOADING"></app-loading-panel>
            <div v-if="this.currentStatus === status.FETCHED">
                            <div class="col-12 text-center">
                                <div class="col-12 pokemon-image">
                                    <img :src="this.data.image">
                                </div>
                                <div><h5 class="m-0">{{ this.data.name }}</h5></div>
                                       <h3>Abilities</h3>
                                <div class="abilities">
                                <div class="ability" 
                                    v-for="(value, index) in data.abilities"
                                    :key="'value'+index">
                                    {{ value.ability.name }}
                                </div>
                                </div>
                                </div>
                            </div>
                        </div>
</template>

<script>

import LoadingPanel from './LoadingPanel';
import { status } from '../config';

export default {
    name: "PokemonDetail",

    components: {
            appLoadingPanel: LoadingPanel
        },
        created() {
        	this.fetchData();
        },
        data() {
        	return {
        	    data: {
        	    	number: '',
        	    	name: '',
                    image: '',
                },
                status: status,
                currentStatus: status.LOADING
            }
        },
        watch: {
	        '$route': 'fetchData'
        },
        methods: {
            fetchData() {
                this.currentStatus = status.LOADING;
                this.$store.dispatch( 'fetchPokemonDetails', this.$route.params.id).then(data => {
                    this.currentStatus = status.FETCHED;
                    this.mountData(data);
                }).catch(error => {
                    console.log(error);
                });
            },
            mountData(data) {
                this.data = data;
                this.data.image = require(`../images/pokemons/${data.number}.png`);
            }
        }

    }
</script>

<style scoped>
    .pokemon-image img {
        width: 100px;
    }
</style>
