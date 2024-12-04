<template>

    <section class="display">
        <strong class="tempo">{{ tempoDecorrido }}</strong>
    </section>
</template>


<script lang="ts">
    import { defineComponent } from 'vue';

    export default defineComponent({        
        name:'CronometroRelogio',

        props:{
            tempoEmSegundos:{
                type:Number,
                default:0
            }
        },
        computed: {
        //adicionando um tempo decorrido para o conometro 
        tempoDecorrido () : string{            
            return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11,8)
        }
         },   
    })
</script>

<style scoped>
 .tempo{
    color:rgb(194, 177, 177)
 }
 .display{
    color:var(--texto-primario);
 }
</style>