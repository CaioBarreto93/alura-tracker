<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarter">
      <FormularioTarefa @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <TarefaComponent v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
        <BoxComponent v-if="listaEstaVazia">
          Você não está muito produtivo hoje :( !!!
        </BoxComponent>
      </div>
    </div>

  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import BoxComponent from './components/BoxComponent.vue';
import FormularioTarefa from './components/FormularioTarefa.vue';
import TarefaComponent from './components/TarefaComponent.vue';
import ITarefa from './interface/ITarefa'


export default defineComponent({
  name: 'App',
  data() {
    return {
      tarefas: [] as ITarefa[]
    }
  },
  computed: {
    listaEstaVazia () : boolean{
        return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa): void {
      this.tarefas.push(tarefa)
    }
  },
  components: {
    BarraLateral,
    FormularioTarefa,
    TarefaComponent,
    BoxComponent
  }
});
</script>

<style>
.lista{
  padding: 1rem;
}
</style>
