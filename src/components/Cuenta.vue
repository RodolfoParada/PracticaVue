<template>
 <h2>Tipo de cuenta: {{cuenta}} </h2>
 <h2>Saldo: {{saldo}} </h2>
 <h2>Cuenta {{ estado ? 'Activa' : 'Desactivada' }}</h2> 
 <h2></h2> 

  <div v-for="(item, index) in servicios" :key="index">
   {{( index + 1)}} - {{ item }}
 </div>
 <AccionSaldo 
        texto="Aumentar Saldo"  
        @accion="aumentar"/>

 <AccionSaldo 
         texto="Disminuir Saldo"
         @accion="disminuir"
         :desactivar="desactivar"/>

</template>

<script>
import AccionSaldo from '../components/AccionSaldo.vue'
export default {
    name: 'CueNta',
    components: {
        AccionSaldo
    },
  data() {
    return {
       saldo: 1000,
       cuenta: 'visa',
       estado: true,
       servicios: ['pagos' , 'giros', 'transferencias'],
       desactivar: false
    }
  },
  methods:{
    aumentar(){
       this.saldo = this.saldo + 100
       this.desactivar = false
    },
    disminuir(){
        if(this.saldo === 0) {
            this.desactivar = true
            alert('Saldo Agotado')
            return
        }
        this.saldo = this.saldo - 100

    }
  }
}
</script>

<style>

</style>