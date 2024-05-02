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

<div class="card p-0" style="width: 18rem;">
  <div class="img-wrapper">
    <img :src="project.image ? 'http://127.0.0.1:8000/storage/' + project.image : '/img/fallback-image-one.jpg'" class="card-img-top" alt="...">
  </div>
  <div class="card-body">
    <h5 class="card-title mb-3">{{ project.name }}</h5>
    <!-- <p class="card-text">{{ project.description }}</p> -->
    <p class="card-text mb-3" v-if="project.type != null">{{ project.type.title }}</p>
    <div class="d-flex flex-wrap gap-2 mb-3">
      <small class="card-text" v-for="technology in project.technologies">{{ technology.title }}</small>
    </div>
    <router-link :to="{name: 'single-project', params: {slug: project.slug}}" class="btn btn-info">Mostra Progetto</router-link>
  </div>
</div>

</template>

<style lang="scss">
  .card{
    position: relative;
     width: calc(100% / 4 - 20px * 4 / 3);

    .img-wrapper{
      width: 100%;
      height: 200px;

      img{
        width: 100%;
        height: 100%;
        object-fit: cover;
      }
    }

    .card-body{
      position: absolute;
      top: 0;
      left: 0;

      width: 100%;
      height: 100%;
      display: none;

      background-color: rgba(0, 0, 0, 0.6);
      color: white;
    }

    &:hover{

      .card-body{
        display: flex;
        flex-direction: column;
      }
    }
  }



</style>