<template>
  <button @click="(accion)" :disabled="desactivar"> {{texto}}</button>
  
</template>

<script>
export default {
    name: 'accionCuenta',
    props:{
        texto: String,
        desactivar: {
            type: Boolean,
            default: false
        }
    },
    data() {
        return {
            
        }
    },
    methods: {
        accion(){
           this.$emit('accion')            
        },
      
    }
}
</script>

<style>

</style>