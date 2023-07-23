<template>
    <div class="container">
        <div class="row">
            <h3>A continuación podrás ver tu opinión</h3>
            <div class="col-12" v-for="(opinion, index) in opiniones" :key="index">
                <br>
                <div class="accordion" id="accordionExample">
                    <div class="accordion-item">
                        <h2 class="accordion-header">
                            <button class="accordion-button" type="button" data-bs-toggle="collapse"
                                :data-bs-target="`#collapse${index}`" aria-expanded="true" aria-controls="collapseOne">
                                Opinion creada por {{ opinion.name }}
                            </button>
                        </h2>
                        <div :id="`#collapse${index}`" class="accordion-collapse collapse show"
                            data-bs-parent="#accordionExample">
                            <div class="accordion-body text-start">
                                <strong>Opinión,</strong>
                                {{ opinion.opinion }}
                            </div>
                            <div>
                                <button type="submit" class="btn btn-warning" @click.prevent="editarOpinion(index)">Editar</button>
                                <button type="submit" class="btn btn-danger" @click.prevent="borrarOpinion(index)">Borrar</button>
                            </div>
                            
                        </div>
                    </div>

                </div>
            </div>
        </div>

    </div>
</template>

<script>
export default {
    name: 'opinion-juego',
    props: {
        opiniones: {
            type: Array,
            required: true
        }
    },
    data: function () {
        return {}
    },
    // computed: {},
    methods: {
        editarOpinion(index) {
            this.$emit('editOpinion', index)
        },
        borrarOpinion(index){
            this.$emit('deleteOpinion', index)
        }
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
.btn{
    margin: 0 4px 20px 10px;
}
</style>