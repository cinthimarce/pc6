<template>
    <div>
        <div v-if="nombre == ''">
            <DatosUser @obtenerDatos="obtenerNombres"/>
        </div>
        
    </div>


</template>

<script>
import DatosUser from '@/components/DatosUser.vue'

export default {
    name: 'admin',
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