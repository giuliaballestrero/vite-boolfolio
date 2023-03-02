<script>
import axios from 'axios';
//to do -- import card component 

export default {

  name: 'AppMain',

  components: {
//to do -- import card component
  },

  data () {
    return {
      projects: [],
      loading: false,
      urlAddress: 'http://127.0.0.1:8000/api/projects',
    }
  },

  methods: {
    getprojects () {
      axios.get(this.urlAddress, {
        params: {
          //
        }
      })
      .then((response) => {
        console.log(response.data.results.data);
        this.projects= response.data.results.data;
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

        <div class="row">
          <div class="col-12">
            <h1 class="pb-5">Projects list:</h1>
          </div>
        </div>

        <div class="row">
          <div class="col-3" v-for="project in projects">
            <div class="card" style="width: 18rem;">
              <span class="card-header">{{ project.slug }}</span>
              <span>{{ project.type.name }}</span>
              <img :src="project.thumb" class="card-img-top" :alt="project.title">
              <div class="card-body">
                <h5 class="card-title">{{ project.title }}</h5>
                <p class="card-text">{{ project.description }}</p>
                <p class="card-text">{{ project.creation_date }}</p>
                <p>
                  <span class="me-2" v-for="technology in project.technologies">
                    {{ technology.name }}
                  </span>
                </p>
                <a href="#" class="btn btn-primary">Show more</a>
              </div>

            </div>
          </div>
        </div>

      </div>
  </section>

</template>

<style lang="scss" scoped>


</style>
