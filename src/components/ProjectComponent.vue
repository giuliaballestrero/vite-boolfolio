<script>

    export default {

        name: 'ProjectComponent',
    
        props: {
            'project': {
                type: Object,
                required: true,
            }
        },

        data () {
        return {
        //
        }
        }
    }
</script>

<template>
        <div class="card text-center mb-3 single-card p-3">
            <h2 class="card-title fw-bold pt-2">
                {{ project.title }}
            </h2>

            <div class="card-body m-3">
                

                <img :src="project.thumb" class="img-thumbnail" :alt="project.title">

                <p class="card-text pt-4 mb-4">
                    {{ project.description }}
                </p>
                <p class="fw-bold">
                    Type: 
                    <a href="" class="btn btn-disabled rounded-pill fw-bold ms-2">
                        {{project.type.name}}
                    </a>
                </p>

                <span class="fw-bold me-2">Made with (&hearts;):
                    <a class="btn btn-disabled rounded-pill fw-bold me-2 mb-1"  v-for="technology in project.technologies">
                        #{{technology.name}}
                    </a>  
                </span>
            </div>
            
            <div class="card-footer text-muted">
                Created on {{ project.creation_date }} - Proj. id: {{ project.slug }}
            </div>
        </div>   
</template>

<style lang="scss" scoped>

.single-card {
    width: calc(100% / 3 - 2rem);
    margin: 1rem;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    border-radius: 30px;
    box-shadow: rgba(50, 50, 93, 0.25) 0px 50px 100px -20px, rgba(0, 0, 0, 0.3) 0px 30px 60px -30px;
}

.card-footer {
    background-color: #aba9ee8d;
    color: white!important;
    font-weight: bold;
}

a {
    border: 1px solid black;
}

</style>
