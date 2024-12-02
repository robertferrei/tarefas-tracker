<template>
     <div class="is-flex is-align-items-center is-justify-content-space-between">
                    <CronometroRelogio :tempoEmSegundos="tempoEmSegundos" :disabled="cronometroRodando"/>
                    <button class="button" @click="iniciar">
                        <span class="icon">
                            <i class="fas fa-play"></i>
                        </span>
                        <span>play</span>
                    </button>
                    <button class="button" @click="finalizar" :disabled="!cronometroRodando">
                        <span class="icon">
                            <i class="fas fa-stop"></i>
                        </span>
                        <span>stop</span>
                    </button>

                </div>
</template>




<script lang="ts">
import { defineComponent } from 'vue';
import CronometroRelogio from './CronometroRelogio.vue';

export default defineComponent({
    name: 'TemporizadorTempo',
    emits:['aoTemporizadorFinalizado'],
    components:{ CronometroRelogio },

    data() {
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando:false,
        }
    },
  

    methods: {
        //iniciando o cronometro
        iniciar() {
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos += 1
            }, 1000)
        this.cronometroRodando = true
        },
        //finalizando  o cronometro 
        finalizar() {            
            clearInterval(this.cronometro)
            this.cronometroRodando = false
            this.$emit('aoTemporizadorFinalizado',this.tempoEmSegundos)
            this.tempoEmSegundos = 0
        }
    }
})
</script>
