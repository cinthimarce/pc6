<template>
    <div>
        <div class="error">
            <h1>Error 404</h1>
            <h1>Page NotFound</h1>
            <router-link to="/"><button>Regresar a inicio</button></router-link>
            <router-view/>
        </div>
    </div>
</template>

<script>
export default {
    name: 'not-found',
    // props: {},
    data: function(){
        return {}
    },
    // computed: {},
    //methods: {}
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>

<style scoped>
    .error{
        width: 100%;
        height: 94vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-image: url("@/assets/img/error.jpg");
        background-size: cover;
        background-position: center;
    }
    .error h1{
        font-family: 'Handjet', cursive;;
        font-size: 4rem;
        font-weight: 700;
        color: white;
    }
    .error button{
        
        background: yellow;
        border: none;
        border-radius: 5px;
        width: 200px;
        padding: 20px;
    }
</style>