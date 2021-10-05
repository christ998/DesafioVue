<template>
  <table class="table is-bordered is-striped is-fullwidth">

    <thead>
    <tr>
      <th>Nombre</th>
      <th>Descripcion</th>
      <th>Precio</th>
      <th></th>
      <th></th>
    </tr>
    </thead>

    <tbody>
    <tr v-for="(item, index) in producto">
      <th>{{ item.nombre }}</th>
      <th>{{ item.descripcion }}</th>
      <th>{{ item.precio }}</th>
      <td>
        <b-button label="Editar" type="is-primary"
                  @click="cardModal(item.nombre, item.descripcion, item.precio, index)"/>
      </td>
      <td>
        <b-button label="Eliminar" type="is-danger" @click="deleteData"/>
      </td>
    </tr>
    </tbody>
  </table>
</template>

<script>
import ModalForm from "./ModalForm";

export default {
  name: "ListadoProductos",
  components: {
    ModalForm
  },

  data() {
    return {
      producto: Array,
    }
  },
  methods: {
    cardModal(name, desc, price, index) {
      this.$buefy.modal.open({
        parent: this,
        component: ModalForm,
        hasModalCard: true,
        trapFocus: true,
        props: {
          nombre: name,
          descripcion: desc,
          precio: price,
          indice: index
        }
      })
    },
    deleteData() {
      var r = confirm('Desea borrar este producto?')
      if (r){
        var productos = JSON.parse(localStorage.getItem("productos"))
        productos.splice(this.indice, 1)
        localStorage.setItem("productos", JSON.stringify(productos))
        location.reload()
      }


    }
  },
  created() {
    if (process.client) {
      this.producto = localStorage.getItem('productos') ? JSON.parse(localStorage.getItem('productos')) : ''

    }
  }
}
</script>

<style>

</style>
