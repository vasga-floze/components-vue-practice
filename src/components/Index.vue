<template lang="html">

  <section class="src-components-index">
    <h1 >{{titulo}}</h1>
    <div class="container">
      <Register/>
    </div>
  </section>

</template>

<script lang="js">
import Register from './Register.vue'


  export default  {
    name: 'src-components-index',
    components:{
      Register,
    },
    props: {
      titulo:String
    },
    mounted () {

    },
    BeforeCreate(){

    },
    created(){

    },
    data () {
      return {

      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-index {
    color: black;
  }
</style>
