<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulario para criação de uma nova tarefa">
                <input type="text" class="input" placeholder=" Qual tarefa voce deseja iniciar ?">
            </div>

            <div class="column">
                <div class="is-flex is-align-items-center is-justify-content-space-between">
                    <CronometroRelogio :tempoEmSegundos="tempoEmSegundos"/>
                    <button class="button" @click="iniciar">
                        <span class="icon">
                            <i class="fas fa-play"></i>
                        </span>
                        <span>play</span>
                    </button>
                    <button class="button" @click="finalizar">
                        <span class="icon">
                            <i class="fas fa-stop"></i>
                        </span>
                        <span>stop</span>
                    </button>

                </div>
            </div>

        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CronometroRelogio from './CronometroRelogio.vue';

export default defineComponent({
    name: 'FormularioCadastro',
    components:{ CronometroRelogio },

    data() {
        return {
            tempoEmSegundos: 0,
            cronometro:0,
        }
    },
  

    methods: {
        //iniciando o cronometro
        iniciar() {
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos += 1
            }, 1000)            
        },
        //finalizando  o cronometro 
        finalizar() {
            clearInterval(this.cronometro)                          
        }
    }
})
</script>