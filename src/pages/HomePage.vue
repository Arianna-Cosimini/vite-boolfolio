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

      projects: [],

      isLoading: false,

      apiLinks: [],

      apiPageNumber: 1,

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


        if(pageNumber=="&laquo; Previous" && this.apiPageNumber > 1){

                    
          this.apiPageNumber -- ;

        } else if(pageNumber=="Next &raquo;" && this.apiPageNumber < 4) {

          
          this.apiPageNumber ++ ;
          
        } 

        if(!isNaN(pageNumber)){

          this.apiPageNumber = pageNumber;
        }
        

        this.apiCall();
        
      },
    },

  }
</script>

<template>
  <div class="container py-5 ">
    <h2 class="mb-5 text-center fw-bold text-uppercase">I miei progetti</h2>

    <div v-if="!isLoading" class="row gap-4 justify-content-center">
      <ProjectItem class="col-auto" v-for="currentProject in projects" :project="currentProject">
      </ProjectItem>

      <div id="pagination">

        <ul class="d-flex gap-2 justify-content-center">

          <li v-for="link in apiLinks" v-html="link.label" @click="changeApiPage(link.label)"
            :class="link.label == apiPageNumber ? 'active' : ''">

          </li>

        </ul>

      </div>

    </div>
    <div v-else>
      <div class="spinner-border" role="status">
        <span class="visually-hidden">Loading...</span>
      </div>
    </div>

  </div>

</template>

<style lang="scss" scoped>
h2 {
  font-size: 50px;
  margin-bottom: 0;
  background-image: linear-gradient(to right, #bc38fe, #699ffc);
  /* Colore sfumato */
  -webkit-background-clip: text;
  /* Applico la sfumatura al testo */
  -webkit-text-fill-color: transparent;
  /* Nascondo il colore del testo */
}

#pagination {
  margin-top: 100px;
  padding-top: 20px;

  ul {

    list-style-type: none;
    padding: 0;

    li {

      padding: 8px 16px;
      border: 1px solid #699ffc;

      text-decoration: none;
      color: white;

      transition: all .3s ease;

      cursor: pointer;

      &:hover,&.active {
        background-color: #bc38fe;
        color: black;
      }

    }
  }
}
</style>