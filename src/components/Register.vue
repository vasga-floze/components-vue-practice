<template lang="html">

  <section class="src-components-register">
    <h1>CRUD Register and List</h1>
      <b-card-group title="New Register">
        <b-card>
          <b-form>
            <b-row class="my-1">
              <b-col sm="2">
                <label>Nombre:</label>
              </b-col>
              <b-col sm="10">
                <b-form-input v-model="name" placeholder="Category Name"></b-form-input>
              </b-col>
            </b-row>

            <b-row class="my-1">
              <b-col sm="2">
                <label>Description:</label>
              </b-col>
              <b-col sm="10">
                <b-form-input v-model="description" placeholder="Description"></b-form-input>
              </b-col>
            </b-row>

            <b-row class="my-1">
                <b-col sm="2">
                  <b-button type="button" variant="success" @click="add()">Submit</b-button>
                </b-col>
            </b-row>
          </b-form>

        </b-card>

        <b-card title="Registers" header-tag="header" footer-tag="footer">
          <b-card-text><List :cantidad="cantidad" :data="data" @update="updateCount"/></b-card-text>
        </b-card>

    </b-card-group>
    
  </section>

</template>

<script lang="js">
import List from './List.vue'

  export default  {
    name: 'src-components-register',
    props: [],
    components:{
      List 
    },
    mounted () { 

    },
    data () {
      return {
        name: '',
        description: '',
        data:[],
        cantidad:0

      }
    },
    methods: {
      add(){
        this.data.push({
          /*Hala los datos de los input con v-model y hace el push al array data
            pasandolos como clave valor */
            
          name:this.name, description:this.description
        });

        //Enviar el arreglo hacia el localStorage
        localStorage.setItem('dataArray', JSON.stringify(this.data));
        /*
        --> The JSON.stringify() method converts a JavaScript object
            or value to a JSON string.
         
        --> The setItem() method of the Storage interface, when passed a key name
            and value, will add that key to the given Storage object, or update that key's value if it already exists.
            => storage.setItem(keyName, keyValue);
         */
        //Pintar el numero del tamanio del arreglo
        this.cantidad = this.data.length;
      },
      updateCount(value){
        //este metodo se va a amanipular atraves del componente hijo
        this.cantidad = value;
      }
    },
    computed: {

    },
    created(){
      //Se evalua en esta etapa si existe data en el localStorage consultando la clave dataArray
      //para ello se recupera la data del localStorage y se almacena en una variable
      //para poder evaluar si esta vacio o no.
      let dataArray = JSON.parse(localStorage.getItem('dataArray'));
      if(dataArray===null){
        this.data=[]; //Si es null se crea un nuevo espacio
      }else{
        this.data=dataArray; //Si no es vacio se mantiene la data para seguir agregando items
      }
    }
}


</script>

<style scoped lang="css">
  .src-components-register {
    color: darkgreen;
  }
</style>
