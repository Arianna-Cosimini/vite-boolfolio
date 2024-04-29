<script>
import axios from 'axios';

export default {
    name: "ProjectItem",
    
    props:{
        project: Object,
        
    },

    data() {
        return {
            
            
        }
    },

        
}


</script>

<template>

<div class="card" style="width: 18rem;">
  <img :src="'http://127.0.0.1:8000/storage/' + project.image" class="card-img-top" alt="...">
  <div class="card-body">
    <h5 class="card-title">{{ project.name }}</h5>
    <p class="card-text">{{ project.description }}</p>
    <p class="card-text">{{ project.type.title }}</p>
    <p class="card-text" v-for="technology in project.technologies">{{ technology.title }}</p>
  </div>
</div>

</template>

<style lang="scss">




</style>