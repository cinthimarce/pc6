<template>
    <div class="container col-12 ">
        <div v-if="nombre == ''">
            <DatosUser @obtenerDatos="obtenerNombres" />
        </div>
        <div v-else class="usuario-datos col-sm-2">
            <div class="usuario">
                <span class="mdi mdi-account-circle"></span>
                <h3>Bienvenid@</h3>
                <h4>{{ nombre }} {{ apellido }}</h4>
            </div>

            <div class="cuenta container text-start">
                <br>
                <h2>Resumen de tu cuenta</h2>
                <h5>Le diste me gusta al juego <strong>{{game}}</strong></h5>
                <br>
                <div class="card">
                    <h5 class="card-title">¿Deseas comprar coins para este juego?</h5>
                    <div class="card-body text-center">
                        <button class="btn btn-warning" @click="add_coins">
                            <span class="mdi mdi-circle-multiple"></span> Agregar coins</button>
                        <hr>
                        <h5 class="text-start">Cantidad de coins comprados</h5>
                        <div class="progress" role="progressbar" aria-label="Success example" aria-valuenow="25"
                            aria-valuemin="0" aria-valuemax="100">
                            <div :class="[bg_color]" class="progress-bar" :style="coins">${{porcentaje}}</div>
                        </div>
                    </div>
                </div>
                <div class="col-12 mt-4 d-flex gap-1">
                    <div class="card col-4 bg-success">
                        <div class="card-title m-2">
                            <h5 class="fw-semibold text-center">% de finalizacion del juego</h5>
                        </div>
                        <hr>
                        <div class="card-body d-flex justify-content-center">
                            <h4>17%</h4>
                            <span class="mdi mdi-star-half"></span>
                        </div>
                    </div>
                    <br>
                    <div class="card col-4 bg-warning">
                        <div class="card-title m-2">
                            <h5 class="fw-semibold text-center">Logros en el juego</h5>
                        </div>
                        <hr>
                        <div class="card-body d-flex justify-content-center">
                            <h4>116</h4>
                            <span class="mdi mdi-trophy"></span>
                        </div>
                    </div>
                    <br>
                    <div class="card col-4 bg-info">
                        <div class="card-title m-2">
                            <h5 class="fw-semibold text-center">Recompensas</h5>
                        </div>
                        <hr>
                        <div class="card-body d-flex justify-content-center">
                            <h4>200</h4>
                            <span class="mdi mdi-medal"></span>
                        </div>
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
import DatosUser from '@/components/DatosUser.vue'


export default {
    name: 'admin-comp',
    props: ['game'],
    data: function () {
        return {
            nombre: '',
            apellido: '',
            coins: {
                width: "0%"
            },
            bg_color:'',
            porcentaje: ''

        }

    },
    //computed:{}

    methods: {
        obtenerNombres(datos) {
            this.nombre = datos.nombre;
            this.apellido = datos.apellido;
        },
        add_coins(){
            let expression = /[\d]+/
            let porcentaje = this.coins.width.match(expression)
            
            console.log(porcentaje);
            
            if(porcentaje <=101){
                this.coins.width = (Number(porcentaje[0])+25)+'%'
                this.porcentaje = (Number(porcentaje[0])+25)
                this.get_bg_color()
            }
        },
        get_bg_color(){
            let expression = /[\d]+/
            let porcentaje = this.coins.width.match(expression)
            
            if(porcentaje >0){
                this.bg_color = 'bg-success'
            }
            if(porcentaje >25){
                this.bg_color = 'bg-warning'
            }
            if(porcentaje >50){
                this.bg_color = 'bg-danger'
            }
            if(porcentaje >75){
                this.bg_color = 'bg-info'
            }
        },
        
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
.mdi {
    color: black;
}

.mdi-account-circle {
    color: white;
    font-size: 50px;
    margin-right: 8px;
}
.mdi-star-half{
    font-size: 50px;
}
.mdi-trophy{
    font-size: 50px;
}
.mdi-medal{
    font-size: 50px;
}

.card-title {
    margin-top: 13px;
}

.usuario-datos {
    width: 100%;
    height: 100%;
    display: flex;
}

.usuario {
    background: black;
    color: white;
    width: 30%;
    display: flex;
    flex-direction: column;
    align-items: center;
    height: 92vh;
    padding-top: 25px;
}

.usuario img {
    width: 20%;
    background: #ccc;
    border-radius: 50%;
}
</style>