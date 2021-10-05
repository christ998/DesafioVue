<template>
  <div>
    <formulario-agregar-componente></formulario-agregar-componente>
    <div class="container mt-4">
      <listado-productos></listado-productos>

    </div>
  </div>

</template>

<script>
import FormularioAgregarComponente from "../components/FormularioAgregarComponente";
import ListadoProductos from "../components/ListadoProductos";

export default {
  components: {ListadoProductos, FormularioAgregarComponente}
}
</script>
