<script>
    export default {
        name: 'AppHeader'
    }
</script>

<template>
    <header>
        <nav class="navbar navbar-expand-lg">

            <div class="container-fluid">

                <a class="navbar-brand" href="#">
                    <img src="https://static.vecteezy.com/system/resources/previews/014/487/676/original/clean-modern-fox-logo-simple-minimal-animal-icon-vector.jpg" alt="fox-logo">
                </a>

                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>

                <div class="collapse navbar-collapse" id="navbarNav">
                    <ul class="navbar-nav text-light">

                        <li class="nav-item">
                            <RouterLink :to="{name:'home'}" class="nav-link active" aria-current="page" href="#">
                                Home
                            </RouterLink>
                        </li>

                        <li class="nav-item">
                            <router-link :to="{name:'projects'}" class="nav-link" href="#">
                                Projects
                            </router-link>
                        </li>

                        <li class="nav-item">
                            <router-link :to="{name:'about-us'}" class="nav-link" href="#">
                                About Us
                            </router-link> 
                        </li>
                    </ul>
                </div>

            </div>
        </nav>
    </header>
</template>


<style scoped lang="scss">

header {
    box-shadow: rgba(255, 255, 255, 0.1) 0px 1px 1px 0px inset, rgba(50, 50, 93, 0.25) 0px 50px 100px -20px, rgba(0, 0, 0, 0.3) 0px 30px 60px -30px;
}

nav {
    
    a {
        img {
            width: 50px;
        }
    }
}

</style>
