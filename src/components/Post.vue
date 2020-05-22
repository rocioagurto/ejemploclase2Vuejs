<template>
    <div class="container bg-light">
        <h2> Enviando Post</h2>
        <form action="">
            <div class="form-group">
                <label for="Titulo">Titulo del mensaje</label>
                <input type="text" class="form-control" v-model="titulo">
            </div>
            <div class="form-group">
                <label for="mensaje">Escriba el mensaje</label>
                <textarea class="form-control" rows="3" v-model="mensaje"></textarea>
            </div>
            <button type="submit" class="btn btn-primary" @click.prevent="enviar">Enviar</button>
        </form>
        <hr>
        <div v-if="verdadero">
            <h2>Informacion Enviada</h2>
            <table class="table table-striped">
                <thead>
                    <tr>
                        <th>ID</th>
                        <th>Titulo</th>
                        <th>Mensaje</th>

                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(item,index) in enviada" :key="index">
                        <th>{{item.userID}}</th>
                        <td>{{item.title}}</td>
                        <td>{{item.body}}</td>
                    </tr>
                </tbody>
            </table>
        </div>

    </div>
</template>

<script>
    import axios from 'axios'
    export default {
        name: 'Post',
        data() {
            return {
                titulo: '',
                mensaje: '',
                enviada: [],
                verdadero: false
            }
        },
        methods: {
            enviar() {
                let userID = Math.ceil(Math.random() * 100);

                // Fetch es de html5 
                
                // fetch('https://jsonplaceholder.typicode.com/posts', {
                //         method: 'POST',
                //         body: JSON.stringify({
                //             title: this.titulo,
                //             body: this.mensaje,
                //             userId: userID,
                //         }),
                //         headers: {
                //             "Content-type": "application/json; charset=UTF-8"
                //         }
                //     })
                //     .then(response => response.json())
                //     .then(json => {
                //         console.log(json);
                //         alert('Enviado');
                //         this.enviada.push(json);
                //         this.titulo = '';
                //         this.mensaje = '';
                //         this.verdadero = true;
                //     })
                //     .catch(error => console.error(error))
                /* Esta es la direccion donde se mandaran los datos ingresados por el usuario en el formulario, se debe especificar cuales seran los datos:*/
               
            //    Vue recomienda para trabajar con Axios
                axios.post('https://jsonplaceholder.typicode.com/posts', {
                    data: {
                        title: this.titulo,
                        body: this.mensaje,
                        userID: userID
                    }
                }).then(response => {
                    console.log(response.data.data);
                    alert('Enviado');
                    this.enviada.push (response.data.data);
                    this.titulo = '';
                    this.mensaje = '';
                    this.verdadero = true;
                }).catch(error => console.error(error))
            }
        }

    }
</script>

<style>

</style>