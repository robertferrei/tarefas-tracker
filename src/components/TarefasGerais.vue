
<template>
    <BoxQuadrado>
        <div class="columns">
            <div class="column is-7">
                {{tarefa.descricao || 'Tarefa sem descriçao'}}
            </div>
            <div class="column">
                <CronometroRelogio :tempo-em-segundos="tarefa.duracaoEmSegundos"/>
            </div>
            
        </div>
    </BoxQuadrado>
</template>


<script lang="ts">
    import { defineComponent, PropType} from 'vue';
    import CronometroRelogio from './CronometroRelogio.vue';    
    import ITarefa from '../interfaces/ITarefa'
    import BoxQuadrado from './BoxQuadrado.vue';    

    export default defineComponent ({
        name: 'TarefasGerais',
         
        components:{
            CronometroRelogio,
            BoxQuadrado
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


