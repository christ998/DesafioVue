<template>
  <div class=" container has-text-centered">
    <p class="title is-1">Añadir un producto</p>
    <form @submit="send">

      <b-field label="Nombre" horizontal>
        <b-input v-model="producto.nombre" required></b-input>
      </b-field>

      <b-field label="Descripción" horizontal>
        <b-input type="text" minlength="1" v-model="producto.descripcion" required></b-input>
      </b-field>

      <b-field label="Precio" v-model="producto.precio" horizontal>
        <b-input v-model="producto.precio" required validation-message="Solo números positivos" pattern="^[0-9]*$"></b-input>
      </b-field>

      <b-button native-type="submit" type="is-info" >Enviar</b-button>
    </form>
  </div>
</template>

<script>

export default {

  name: "FormularioAgregarComponente",
  data() {
    return {
      producto: {
        nombre: "",
        descripcion: "",
        precio: "",

      }

    }
  },

  methods: {
    send() {

      if (localStorage.getItem("productos")) {
        var productos = JSON.parse(localStorage.getItem('productos'))
        productos.push(this.producto)
        localStorage.setItem('productos', JSON.stringify(productos))

      } else {
        const nuevoProducto = new Array()
        nuevoProducto.push(this.producto)
        localStorage.setItem('productos', JSON.stringify(nuevoProducto))
      }
    }


  }


}


</script>

<style>

</style>
