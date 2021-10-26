<template>
    <div class="container">
        <h2>Resultados</h2>
        <!-- <button class="btn btn-primary" v-on:click="cargarPersonas">Mostrar Resultados</button> -->

    <a v-if="mostrar" v-on:click="cargarPersonas" class="btn btn-success" data-bs-toggle="collapse" href="#collapseResultados" role="button" aria-expanded="false" aria-controls="collapseResultados">
        Mostrar Resultados <i class="fa fa-angle-double-down" aria-hidden="true"></i>
    </a>
    <a v-else v-on:click="cargarPersonas" class="btn btn-orange" data-bs-toggle="collapse" href="#collapseResultados" role="button" aria-expanded="false" aria-controls="collapseResultados">
        Ocultar Resultados <i class="fa fa-angle-double-up" aria-hidden="true"></i>
    </a>
        <div class="collapse" id="collapseResultados">
            <table  class="table table-striped table-hover">
                <tr>
                    <th>Nombre</th>
                    <th>Peso (Kg)</th>
                    <th>Talla (Mt)</th>
                    <th>IMC</th>
                    <th style="text-align:center;">Condición</th>
                    <th>Recomendaciones</th>
                    <th>Accion</th>
                </tr>
                <tr v-for="persona in personas" :key="persona.id" class="animate__animated animate__fadeInDown">
                    <td>{{persona.nombre}} {{persona.apellido}}</td>
                    <td>{{persona.peso}} </td>
                    <td>{{persona.talla}}</td>
                    <td>{{persona.imc}}</td>
                    <td  align="center">{{persona.condicion}}</td>
                    <td>{{persona.recomendacion}}</td>
                    <td>
                        <!-- <button v-on:click="editarPersona(persona.id)">Editar</button> -->
                        <button type="button" class="btn btn-outline-danger" v-on:click="eliminarPersona(persona.id)"><i class="fa fa-trash-o fa-lg"></i> Eliminar</button></td>
                </tr>
            </table>
        </div>
    </div>
</template>

<script>
    export default{
        name: 'Resultados',
        props: {
            token: String,
        },
        ///////otra forma con array function para return implicito
        data: ()=>({
            personas: [],
            mostrar: true
        }),
        methods: {
           async cargarPersonas(){
                const requestOptions={
                    method: "GET",
                    headers: {
                        "Content-Type": "application/json",
                        "Authorization": this.token,
                    }
                };
                const respuesta = await fetch("http://localhost:8082/api/personas", requestOptions)
                this.personas = await respuesta.json();
                const hombres = this.personas.filter(item => item.genero == 'M');
                const mujeres = this.personas.filter(item => item.genero == 'F');
                console.log(hombres);
                console.log(mujeres);
                this.mostrar = !this.mostrar;
                console.log(this.mostrar)
            },
            async eliminarPersona(id){
                const requestOptions={
                    method: "DELETE",
                    headers: {
                        "Content-Type": "application/json",
                        "Authorization": this.token,
                    }
                };
               await fetch(`http://localhost:8082/api/personas/${id}`, requestOptions)
                ////actualizar la tabla para que desaparezca el eliminado
                this.cargarPersonas();
            },
            editarPersona(){
                ////ejecutar el buscar persona que esta en componente <Personas>, 
                ////desde aca se carga al form y no muestra resultado, 
                ///y en buscar de Persona oculte form y muestre solo resultado
            }
        },
    }
</script>

<style scoped>
    
</style>
