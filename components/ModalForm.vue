<template>

  <form @submit="updateData">
    <div class="modal-card" style="width: auto">
      <header class="modal-card-head">
        <p class="modal-card-title">Actualizar</p>
        <button
          type="button"
          class="delete"
          @click="$emit('close')"/>
      </header>
      <section class="modal-card-body">
        <b-field label="Nombre">
          <b-input
            type="text"
            v-model="nombreActualizado"
            placeholder="Nombre"
            required>
          </b-input>
        </b-field>

        <b-field label="Descripcion">
          <b-input
            type="text"
            :value="descripcionActualizada"
            placeholder="Descripcion"
            required>
          </b-input>
        </b-field>
        <b-field label="Precio">
          <b-input
            type="number"
            v-model="precioActualizado"
            placeholder="Precio"
            required>
          </b-input>
        </b-field>

      </section>
      <footer class="modal-card-foot">
        <b-button
          label="Cerrar"
          @click="$emit('close')"/>
        <b-button
          label="Actualizar"
          native-type="submit"
          type="is-primary"/>
      </footer>
    </div>
  </form>
</template>

<script>
export default {
  name: "ModalForm",
  props:['nombre', 'descripcion', 'precio','indice'],
  data(){
    return{
      nombreActualizado: this.nombre,
      descripcionActualizada: this.descripcion,
      precioActualizado: this.precio
    }
  },
  methods:{
    updateData(){
      const productoActualizado = {
        nombre: this.nombreActualizado,
        descripcion: this.descripcionActualizada,
        precio: this.precioActualizado
      }
      console.log(productoActualizado)
      var productos = JSON.parse(localStorage.getItem("productos"))
      productos.splice(this.indice, 1 , productoActualizado)
      localStorage.setItem("productos", JSON.stringify(productos))
    },

  }


}
</script>

<style>

</style>
