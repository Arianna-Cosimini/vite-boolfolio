<script>
  import axios from 'axios';

import ProjectItem from './components/ProjectItem.vue';


  export default {

    components: {
        ProjectItem,
        
    },

    data() {
      return {

        projects: [],

        apiLinks: [],

        apiPageNumber: 2,

        baseApiUrl: 'http://127.0.0.1:8000/api',
      }
    },

    mounted() {
      this.apiCall();
    },

    methods: {
      
      apiCall() {

        axios.get(this.baseApiUrl + '/projects', { 
          params: {
            page: this.apiPageNumber
          }
        }).then(res => {        

           this.projects = res.data.results.data;

           this.apiLinks = res.data.results.links;
        })
      },

      changeApiPage(pageNumber) {
        
        this.apiPageNumber = pageNumber;

        this.apiCall();
      },

    },

  }
</script>

<template>
 <div class="container py-5 ">
  <h1 class="pb-4">Progetti</h1>

  <div class="row gap-4">
    <ProjectItem
    class="col-auto"
    v-for="currentProject in projects"
    :project="currentProject">
    </ProjectItem>

  </div>

 </div>
    
</template>

<style scoped>

</style>
