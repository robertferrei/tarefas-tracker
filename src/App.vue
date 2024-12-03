<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarter">
      <FormularioCadastro @aoSalvarTarefa = "salvarTarefa" />
      <div class="lista">
   
        <TarefasGerais v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>                
        <BoxQuadrado v-if="tarefas.length <=0">
          Voce não esta muito produtivo hoje :(
        </BoxQuadrado>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue'
import FormularioCadastro from './components/FormularioCadastro.vue'
import TarefasGerais from './components/TarefasGerais.vue';
import ITarefa from './interfaces/ITarefa';
import BoxQuadrado from './components/BoxQuadrado.vue';


export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    FormularioCadastro,
    TarefasGerais,
    BoxQuadrado
    
  },
  data(){
    return{
      tarefas: [] as ITarefa[]
    }
  },
  methods:{
    salvarTarefa (tarefa: ITarefa){
      this.tarefas.push(tarefa)
      console.log('tarefas',this.tarefas)
    }
  }

});
</script>

<style >
.lista{
  padding:1.25rem ;
}
</style>
