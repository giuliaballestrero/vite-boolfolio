<script>
//importo il component dei progetti
    import ProjectComponent from '../components/ProjectComponent.vue';
//importo axios
    import axios from 'axios';

export default {
    name: 'projectsList',

    components:{
        ProjectComponent,
    },

    data() {
        return {
            projects: [],
            loading: false,
            urlAddress: 'http://127.0.0.1:8000/api/projects/',
        }
    },
    methods: {
        getProjects(){
            axios.get(this.urlAddress, {
                params: {
                    //
                }
            })
            .then((response) => {
                //console.log(response.data.results.data);
                this.projects = response.data.results.data;
            })
            .catch(function (error) {
                console.warn(error);
            });
        }
    },
    created() {
        this.getProjects();
    },
}
</script>

<template>

    <section>
        <div class="container">

            <h1 class="pb-5 tracking-in-contract text-center pt-5">Projects list:</h1>

            <div class="card-wrapper">
            <!--Qui andranno le card-->
            
                <ProjectComponent 
                    v-for="projectElement in projects" :project="projectElement"
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

.single-card {
    width: calc(100% / 3 - 2rem);
    margin: 1rem;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    border-radius: 30px;
    box-shadow: rgba(50, 50, 93, 0.25) 0px 50px 100px -20px, rgba(0, 0, 0, 0.3) 0px 30px 60px -30px;
}

</style>
