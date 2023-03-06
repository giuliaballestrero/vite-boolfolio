<script>
//importo il component dei progetti
    import ProjectComponent from '../components/ProjectComponent.vue';
//importo axios
    import axios from 'axios';

export default {
    name: 'SingleProject',

    components:{
        ProjectComponent,
    },

    data() {
        return {
            project: null,
            loading: false,
            urlAddress: 'http://127.0.0.1:8000/api/projects/',
        }
    },
    methods: {
        getProject(){
            axios.get(this.urlAddress + this.$route.params.slug, {
                params: {
                    'api_token' : 's6PuirNp2n5r0PuBA2wghrcyTRtDxTvWwHnVrKBllweT6yW8oc3L2dckPzBLa6W09k1ErDJUmkEn4yqXDeeI8xlHBBe6ivIrJKVf',
                }
            })
            .then((response) => {
                //console.log(response.data.results.data);
                this.project = response.data.results;
            })
            .catch(function (error) {
                console.warn(error);
            });
        }
    },
    created() {
        this.getProject();
    },
}
</script>

<template>

    <section>
        <div class="container">
            <h1 class="pb-5 tracking-in-contract text-center pt-5">Project details:</h1>

            <!--Qui andrà il singolo progetto-->
            <ProjectComponent 
                :project="project"
                :isShow="true"
            />
        </div>
    </section>
</template>

<style lang="scss" scoped>

.card-wrapper {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}

//aggiungo un'animazione per il titolo//
.tracking-in-contract {
	animation: tracking-in-contract 1s ease-in both;
}

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