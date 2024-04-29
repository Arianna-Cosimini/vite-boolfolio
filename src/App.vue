<script>
  import axios from 'axios';

  export default {
    data() {
      return {

        projects: [],

        baseApiUrl: 'http://127.0.0.1:8000/api',
      }
    },

    mounted() {
      this.apiCall();
    },

    methods: {
      
      apiCall() {

        axios.get(this.baseApiUrl + '/projects').then(res => {
           this.projects = res.data.results;
           console.log(this.projects);
        })
      }
    },
  }
</script>

<template>
 <div class="container py-5 ">
  <h1>ciao</h1>

 </div>
    
</template>

<style scoped>

</style>
