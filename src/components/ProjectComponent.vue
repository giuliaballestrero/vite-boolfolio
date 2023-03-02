<script>

export default {

    name: 'ProjectComponent',
  
    props: {
        project: Object,
    },

    data () {
    return {

    }
    }
}
</script>

<template>
        <div class="card text-center mb-3">
            <div class="card-body p-3 m-3">
                <h2 class="card-title fw-bold p-3">
                    {{ project.title }}
                </h2>

                <img :src="project.thumb" class="img-thumb" :alt="project.title">

                <p class="card-text pt-4 mb-4">
                    {{ project.description }}
                </p>
                <p class="fw-bold">
                    Type: 
                    <a href="" class="btn btn-disabled rounded-pill fw-bold ms-2">
                        {{project.type.name}}
                    </a>
                </p>

                <span class="fw-bold me-2">Made with (&hearts;): </span>
                    <a class="btn btn-disabled rounded-pill fw-bold me-2" v-for="technology in project.technologies">
                        #{{technology.name}}
                    </a> 
            </div>
            
            <div class="card-footer text-muted">
                Created on {{ project.creation_date }} - Proj. id: {{ project.slug }}
            </div>
        </div>   
</template>

<style lang="scss" scoped>

</style>
