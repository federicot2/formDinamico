<template>
  <form>
    <div class="row">
      <div class="col-md-4">
        <label>
          Nombre:
          <input type="text" v-model="nombre" class="form-control" />
        </label>
      </div>
      <div class="col-md-4">
        <label>
          Apellido:
          <input type="text" v-model="apellido" class="form-control" />
        </label>
      </div>
      <div class="col-md-4">
        <label>
          Correo electrónico:
          <input type="email" v-model="email" class="form-control" />
        </label>
      </div>
    </div>

    <div class="row">
      <div class="col-md-4">
        <label>
          Teléfono:
          <input type="tel" v-model="telefono" class="form-control" />
        </label>
      </div>
      <div class="col-md-4">
        <label>
          Dirección:
          <input type="text" v-model="direccion" class="form-control" />
        </label>
      </div>
      <div class="col-md-4">
        <label>
          Seleccione una opción:
          <select v-model="opcion" class="form-select">
            <option value="">Seleccione</option>
            <option value="entrada">Entrada</option>
            <option value="salida">Salida</option>
          </select>
        </label>
      </div>
    </div>

    <div class="row" v-if="opcion === 'entrada'">
      <div class="col-md-4" v-for="id in idsEntrada" :key="id">
        <label>
          {{ id }}:
          <input type="text" v-model="identificadoresEntrada[id]" class="form-control" />
        </label>
      </div>

      <div class="col-md-4">
        <label>
          Seleccione una opción:
          <select v-model="opcionEntrada" class="form-select">
            <option value="">Seleccione</option>
            <option v-for="option in idsEntradaSelect" :key="option" :value="option">{{ option }}</option>
          </select>
        </label>
      </div>

    </div>

    <div class="row" v-if="opcion === 'salida'">
      <div class="col-md-4" v-for="id in idsSalida" :key="id">
        <label>
          {{ id }}:
          <input type="text" v-model="identificadoresSalida[id]" class="form-control" />
        </label>
      </div>
    </div>

    <div class="row" v-if="opcionEntrada === 'Semestre'">
      <div class="col-md-4" v-for="id in idsEntradaSemestre" :key="id">
        <label>
          {{ id }}:
          <input type="text" v-model="identificadoresEntradaSemestre[id]" class="form-control" />
        </label>
      </div>
    </div>
    <br>
    <div class="row">
      <div class="col-md-12">
        <button type="submit" class="btn btn-primary">Enviar</button>
      </div>
    </div>
  </form>
</template>


<script>
export default {
  data() {
    return {
      nombre: '',
      apellido: '',
      email: '',
      telefono: '',
      direccion: '',
      opcion: '',

      opcionEntrada: '',//select en entrada

      idsEntrada: ["Pasaporte","Otra Opcion","ETC"], // Identificadores para opción entrada

      idsEntradaSemestre:["Opcion0","Opcion1","Opcion2"],
      identificadoresEntradaSemestre:{},

      idsEntradaSelect: ["Semestre", "Investigacion","Otra opcion"],//datos de select entrada

      identificadoresEntrada: {}, // Objeto vacío para almacenar los identificadores de entrada
      idsSalida: ["Cedula", "Pasaporte"], // Identificadores para opción salida
      identificadoresSalida: {} // Objeto vacío para almacenar los identificadores de salida
    }
  }
}
</script>
