<template>
  <!-- <ul class="list">
    <li v-for="(item, i) in elements" :key="i">
      ID: {{item.id}} - {{item.name}} | childrens: 
      <span v-for="(children, j) in item.childrens" :key="'child' + j">
        {{children}}, 
      </span>
    </li>
  </ul>
   -->
   <div id="formulario-usuario">
      <form @submit.prevent="enviarFormulario">
        <div class="container">
            <div class="row">
                <div class="col-md-4">
                    <div class="form-group">
                        <label  >Nombre</label>
                            <input
                                placeholder="Nombre"
                                v-model="usuario.nombre"
                                type="text"
                                class="form-control"
                                :class="{ 'is-invalid': procesando && nombreInvalido }"
                                @focus="resetEstado"
                            />
                    </div>
                </div>
            <div class="col-md-4">
                <div class="form-group">
                    <label>Apellido</label>
                    <input
                        placeholder="Apellido"
                        v-model="usuario.apellido"
                        type="text"
                        class="form-control"
                        :class="{ 'is-invalid': procesando && apellidoInvalido }"
                        @focus="resetEstado"
                    />
          </div>
      </form>
                <div class="container">
                  <div class="row">
                      <div class="col-md-12">
                          <div v-if="error && procesando" class="alert alert-danger" role="alert">
                              Debes rellenar todos los campos!
                            </div>
                            <div v-if="correcto" class="alert alert-success" role="alert">
                                La persona ha sido agregada correctamente!
                            </div>
                        </div>
                    </div>
                </div>
                <div class="form-floating mb-3">
                    <input type="text" class="form-control form-control-sm" id="nombre" v-model="persona.nombre" placeholder="Nombre" required>
                    <label class="text-muted" for="nombre">Nombre: *</label>
                </div>
                <div class="form-floating mb-3">
                    <input type="text" class="form-control form-control-sm" id="apellido" v-model="persona.apellido" placeholder="Apellido" required>
                    <label class="text-muted" for="apellido">Apellido: *</label>
                </div>
                  <!-- <label for="presentacion">Presentación: </label><br>
                <textarea class="form-control" v-model="persona.presentacion" id="presentacion" cols="50" rows="3"></textarea><br> -->
                <!-- <label class="form-check-label" for="admin">Admin: </label><input class="form-check-input" v-model="persona.admin" id="admin" type="checkbox"><br> -->
                <!-- <label for="registro">Fecha Registro: </label><input v-model="persona.fechaRegistro" id="registro" type="date"><br> -->
                <!-- <input type="button" v-on:click="limpiar" value="Limpiar" style="right: center;"><br> -->
                 <!-- <button class="btn btn-primary me-md-2" type="button">Button</button>
                    <button class="btn btn-primary" type="button">Button</button> -->
                    <!-- 
                <div class="form-floating mb-3">
                    <input type="number" class="form-control form-control-sm" id="documento" v-model="persona.numeroDocumento" placeholder="Numero Documento" required>
                    <label class="text-muted" for="documento">Numero Documento: *</label>
                </div> -->
    </div>
</template>

<script>
export default {
  data: () => ({
    elements: [
      { name: "Elemento 1", id: 1, childrens: [1,3,4] },
      { name: "Elemento 2", id: 2, childrens: [3,5,5] },
      { name: "Elemento 3", id: 3, childrens: [5,7,3] }
    ]
  })
};
</script>

<style scoped>
</style>