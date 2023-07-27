<template>
    <div class="container">
        <div class="row justify-content-center">
        <div class="col-12 col-md-4 mb-4" v-for="game in games" :key="game.id">
            <div class="card" style="width: 18rem;">
                <img :src="game.background_image" class="card-img-top img-box" alt="Card image cap">
                <div class="card-body">
                    <h5 class="card-title">{{game.name}}</h5>
                </div>
                <ul class="list-group list-group-flush">
                    <li class="list-group-item">Rating:{{ game.rating }} </li>
                    <li class="list-group-item">Release: {{ game.released }}</li>
                    <li class="list-group-item">Update: {{ game.updated }}</li>
                </ul>
                <div class="card-body">
                    <button class="btn btn-primary" type="submit" @click="redirect(game.name)">Opinar</button>
                    <button class="mdi mdi-heart" @click="redirectAdmin(game.name)"></button>
                </div>
            </div>
        </div>
    </div>
    </div>

</template>

<script>
export default {
    name: 'ListadeJuegos',
    props: {
        games: {
            type: Array,
            required: true
        }
    },
    data: function () {
        return {
            
        }
    },
    // computed: {},
    methods: {
        redirect(name){
            this.$router.push(`/opiniones/${name}`)
        },
        redirectAdmin(game){
            console.log(game);
            this.$router.push(`/administracion/${game}`)

        },
    }
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>
  
<style scoped>
button{
    border-style: none;
}
.mdi {
    color: red;
    padding: 5px;
    font-size: 25px;
}
.img-box{
    height: 160px;
    object-fit: cover;
}
</style>