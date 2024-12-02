
<template>
    <div class="box" has-text-weight-bold>
        <div class="columns">
            <div class="column is-7">
                {{tarefa.descricao}}
            </div>
            <div class="column">
                <CronometroRelogio :tempo-em-segundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </div>
</template>


<script lang="ts">
    import { defineComponent, PropType} from 'vue';
    import CronometroRelogio from './CronometroRelogio.vue';    
    import ITarefa from '../interfaces/ITarefa'    

    export default defineComponent ({
        name: 'TarefasGerais',
         
        components:{
            CronometroRelogio
        },
        props:{
            tarefa: {
                type: Object as PropType <ITarefa>,
                required: true
            }                        
        },
        setup(props){
            console.log('tarefa prop',props.tarefa)
        }
    })
</script>


<style scoped>
 .box{
    background-color: #faf0ca;
 }
 .column{
    color: black;
 }

</style>