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
      <div class="container-fluid">

        <h1 class="pb-5 tracking-in-contract">Projects list:</h1>

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

.card-wrapper {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}

.tracking-in-contract {
	animation: tracking-in-contract 1s ease-in both;
}

//aggiungo un'animazione per il titolo//
 @keyframes tracking-in-contract {
  0% {
    letter-spacing: 1em;
    opacity: 0;
  }
  40% {
    opacity: 0.6;
  }
  100% {
    letter-spacing: normal;
    opacity: 1;
  }
}


</style>
