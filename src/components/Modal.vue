<template>
    <div>
        <!-- Modal -->
        <div class="modal fade" :id="'ventana'+index" data-backdrop="static" data-keyboard="false" tabindex="-1"
            role="dialog" aria-labelledby="staticBackdropLabel" aria-hidden="true">
            <div class="modal-dialog modal-dialog-scrollable">
                <div class="modal-content">
                    <div class="modal-header">
                        <div class="d-block w-100">
                            <img :src="imagen" alt="1" class="img-fluid w-50">
                        </div>
                        <h5 class="modal-title d-block" id="staticBackdropLabel" v-text="nombre"></h5>
                        
                        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                            <span aria-hidden="true">&times;</span>
                        </button>
                    </div>
                    <div class="modal-body">
                    <p v-html="descrip" class="text-justify"></p>
                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-secondary" data-dismiss="modal">Cerrar</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name:'Modal',
        props: ['imagen', 'descrip', 'nombre', 'index']
    }
</script>

<style>

</style>