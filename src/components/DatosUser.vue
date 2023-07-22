<template>
    <div>
        <div class="container ">
            <br>
            <h2>Para ver información ingresa tus datos</h2>
            <br>
            <button class="btn btn-success" @click="obtenerDatos">Ingresar datos</button>
        </div>

    </div>
</template>

<script>


export default {
    name: 'datos-user',
    //props: {},
    data: function(){
        return {
        }
    },
    // computed: {},
    methods: {
        obtenerDatos(){
            let datos = {
                nombre: prompt('Ingrese su nombre: '),
                apellido: prompt('Ingrese su apellido: '),
            }
            this.$emit('obtenerDatos',datos)
        }
    },
    // watch: {},
    //components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>

<style scoped>
    
</style>