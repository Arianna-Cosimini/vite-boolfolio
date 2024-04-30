<script>

import axios from 'axios';

export default {
    name: 'SingleProject',

    data() {
        return {
            project: null,
            projectSlug: null,

            baseApiUrl: 'http://127.0.0.1:8000/api',
        }
    },

    mounted() {

        this.projectSlug = this.$route.params.slug;

        axios.get(this.baseApiUrl + '/projects/' + this.projectSlug).then(res => {

            if (res.data.success) {
                
                this.project = res.data.project
                console.log(this.project)
            } else {

                this.$router.push({name: 'home'})
            }
        })
    },
}

</script>

<template>

    <div class="container p-5" v-if="project">
        <h1>{{ project.name }}</h1>
        <p>{{ project.description }}</p>
        <p>{{ project.type.title }}</p>
        <p v-for="technology in project.technologies">{{ technology.title }}</p>
    </div>
    <div v-else>
        <div class="spinner-border" role="status">
            <span class="visually-hidden">Loading...</span>
        </div>
    </div>

</template>

<style lang="scss">

</style>