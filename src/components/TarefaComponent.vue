<template>
    <BoxComponent>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa?.descricao || 'Tarefa sem descrição '}}
            </div>
            <div class="column">
                <CronometroTarefa :tempoEmSegundos="tarefa?.duracaoEmSegundos" />
            </div>
        </div>
    </BoxComponent>
</template>

<script lang="ts">
import ITarefa from '@/interface/ITarefa';
import { defineComponent, PropType } from 'vue';
import CronometroTarefa from './CronometroTarefa.vue';
import BoxComponent from './BoxComponent.vue'

export default defineComponent({
    name: 'TarefaComponent',
    components: {
        CronometroTarefa,
        BoxComponent
    },
    props:{
        tarefa:{
            type: Object as PropType<ITarefa>,
            require: true
        }
    }
})

</script>