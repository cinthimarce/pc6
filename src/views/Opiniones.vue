<template>
    <div class="container">
        <div class="row">
            <div class="col col-12">
                <form>
                    <br>
                    <h2>Escribe tu opinión para el juego:{{name}}</h2>
                    <br>
                    <div class="mb-3 text-start">
                        <label for="exampleInputEmail1" class="form-label ">Nombre</label>
                        <input type="text" class="form-control" aria-describedby="emailHelp" v-model="user.name">

                    </div>
                    <div class="mb-3 text-start">
                        <label for="exampleInputPassword1" class="form-label ">Opinión</label>
                        <input type="text" class="form-control" v-model="user.opinion">
                    </div>
                    <div class="text-start">
                        <button type="submit" class="btn btn-primary " @click.prevent="editarOpinion" v-if="showEdit">Editar</button>
                        <button type="submit" class="btn btn-primary" @click.prevent="agregarOpinion" v-else>Agregar</button>
                    </div>
                </form>
                <br>
                <div >
                    <opinion :opiniones="opiniones" @editOpinion="editOpinion" @deleteOpinion="deleteOpinion"/>
                </div>
            </div>
        </div>    
    </div>
</template>

<script>
import Opinion from '@/components/Opinion.vue'

export default {
    name: 'component-name',
    props: {
        name: {
            type: String,
            required: true
        }
    },
    data: function () {
        return {
            user: {
                name: '',
                opinion: '',
            },
            opiniones: [],
            showEdit: false,
            editIndex: null
        }
    },
    // computed: {},
    methods: {
        agregarOpinion() {
            if (this.user.name == '' || this.user.opinion == '') {
                alert('faltan campos x rellenar')
                return
            }
            this.opiniones.push({ ...this.user })
            this.user.name = ''
            this.user.opinion = ''
            
        },
        editOpinion(index){
            let my_opinion = {...this.opiniones[index]}
            this.user.name = my_opinion.name
            this.user.opinion = my_opinion.opinion
            this.showEdit = true
            this.editIndex = index
        },
        deleteOpinion(index){
            this.opiniones.splice(index,1) 
        },
        editarOpinion(){
            this.opiniones.splice(this.editIndex,1,{...this.user})
            this.user.name = ''
            this.user.opinion = ''
            this.showEdit = false 
        }

    },
    // watch: {},
    components: {
        Opinion
    },
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>

<style scoped>

</style>