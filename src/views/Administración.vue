<template>
    <div class="container">
        <div v-if="nombre == ''">
            <DatosUser @obtenerDatos="obtenerNombres"/>
        </div>
        <div class="row">
            <div class="col-sm-2">
                <div class="usuario">
                <img src="../assets/img/usuario.png" alt="">
                <h2>Bienvenid@</h2>
                <h3>{{ nombre }} {{ apellido }}</h3>
            </div>
            </div>

        </div>
    </div>


</template>

<script>
import DatosUser from '@/components/DatosUser.vue'


export default {
    name: 'admin-component',
    props: ['name'],
    data: function(){
        return {
            nombre:'',
            apellido:'' 
        }
    },
    computed: {
        gameName(){
            return this.$route.params.id
        }
    },
    methods: {
        obtenerNombres(datos){
            this.nombre = datos.nombre;
            this.apellido = datos.apellido;
        }
    },
    
    // watch: {},
    components: {
        DatosUser
        
    },
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>

<style scoped>
    
</style>