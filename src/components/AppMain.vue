<script>
  //import Axios
  import axios from 'axios';
  import { store } from '../store.js';
  //console.log(store); 

  //import project component
  import ProjectComponent from './ProjectComponent.vue'; 

export default {

  name: 'AppMain',

  components: {
    ProjectComponent
  },

  data () {
    return {
      store,

      projects: [],
      loading: false,
      urlAddress: 'http://127.0.0.1:8000/api/projects',
    }
  },

  methods: {
    //create axios call to show laravel projects
    getprojects () {
      axios.get(this.urlAddress, {
        params: {
          //
        }
      })
      .then((response) => {
        //console.log(response.data.results.data);
        this.store.projectList= response.data.results.data;
    })   
    }
  },
  created() {
    this.getprojects();
  },
    
}


</script>

<template>

  <section>
      <div class="container">

        <h1 class="pb-5">Projects list:</h1>

        <div class="card-wrapper">
          <!--Qui andranno le card-->
        
          <ProjectComponent 
            v-for="projectElement in store.projectList" :project="projectElement"
          />
        </div>

      </div>
  </section>

</template>

<style lang="scss" scoped>


</style>
