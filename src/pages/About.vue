<script>
import axios from 'axios';

import ProjectItem from '../components/ProjectItem.vue';


export default {

    name: 'HomePage',

    components: {
        ProjectItem,

    },

    data() {
        return {
        }
    },

    mounted() {

    },

    methods: {
    },

}
</script>

<template>

    <div class="container py-5">
        <router-link :to="{ name: 'app-projects', params: { slug: projects } }" class="btn btn-info">Mostra
            Progetto</router-link>
    </div>



</template>

<style lang="scss"></style>