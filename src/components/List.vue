<template lang="html">

  <section class="src-components-list">
    <h1>src-components-list Component</h1>
     <h1>Registros <b-badge variant="primary">{{cantidad}}</b-badge></h1>


    <b-table-simple>
        <b-thead>
          <b-th>ID</b-th>
          <b-th>Nombre</b-th>
          <b-th>Descripcion</b-th>
          <b-th></b-th>
          <b-th></b-th>
        </b-thead>
        <b-tbody>
          <b-tr v-for="(registro, index) in data" v-bind:key="registro.index">
              <b-td>{{index}}</b-td>
              <b-td>
                    <b-form-input v-model="registro.name"></b-form-input>
              </b-td>
              <b-td>
                    <b-form-input v-model="registro.description"></b-form-input>
              </b-td>
              <b-td>
                <b-button type="button" @click="del(index)" variant="danger"><b-icon icon="trash"></b-icon></b-button>
              </b-td>
              <b-td>
                <b-button type="button" @click="edit()" variant="success"><b-icon icon="check-square"></b-icon></b-button>
              </b-td>
          </b-tr>

        </b-tbody>
    </b-table-simple>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-components-list',
    props: ['data', 'cantidad'], //aqui en props van las propiedades que se reciben del compomente Register.vue
    mounted () {
    },
    data () {
      return {
      }
    },
    methods: {
      //Este es el metodo para eliminar (Metodo que llamamos desde los botones con los eventos click)
      del(index){
        //con la linea a continuacion quitamos un elemento del array:
        this.data.splice(index,1);

        //Con la linea a continuacion volvemos a asignar el array
        localStorage.setItem('dataArray', JSON.stringify(this.data));

        //Enviar un nuevo valor al componente padre, actualiza el tamaño del array despues de eliminar un item
        this.$emit('update', this.data.length);

        /*
          The splice() method changes the contents of an array by removing or replacing existing elements
          and/or adding new elements.
          Sintaxis:
          let arrDeletedItems = arr.splice(start[, deleteCount[, item1[, item2[, ...]]]])
        */

      },

      //Este es el metodo para actualizar (Metodo que llamamos desde los botones con los eventos click)
      edit(){
        //En este metodo solo volvemos a enviar al localStorage lo que se edita
        localStorage.setItem('dataArray', JSON.stringify(this.data));

        
        //Enviar un nuevo valor al componente padre, actualiza el tamaño del array despues de eliminar un item
        this.$emit('update', this.data.length);
      }
    },
    computed: {
    }
}


</script>

<style scoped lang="css">
  .src-components-list {
    color: slateblue;
  }
</style>
