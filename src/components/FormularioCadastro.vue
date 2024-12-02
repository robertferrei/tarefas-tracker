<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulario para criação de uma nova tarefa">
                <input v-model="descricao" type="text" class="input" placeholder=" Qual tarefa voce deseja iniciar ?">
            </div>
            <div class="column">
                <TemporizadorTempo @ao-temporizador-finalizado="finalizarTarefa"/>               
            </div>

        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TemporizadorTempo from './TemporizadorTempo.vue';

export default defineComponent({
    name: 'FormularioCadastro',
    emits: ['aoSalvarTarefa'],  //emitindo evento no APP.VUE
    components:{ TemporizadorTempo },
    data(){
        return{
            descricao: '',
        }
    },
    methods:{
        finalizarTarefa(tempoDecorrido: number) : void {
            this.$emit('aoSalvarTarefa',{
            duracaoEmSegundos: tempoDecorrido,
            descricao: this.descricao
            })
            this.descricao = ''
        },
    }
})
</script>