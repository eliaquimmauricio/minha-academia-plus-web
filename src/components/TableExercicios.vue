<template>
  <v-card-text class="text-left">
    <h4>{{ items.nomeExercicio }}</h4><br/>
    <span>Execução: {{ items.quantidadeDeSeries }} x {{ items.quantidadeDeRepeticoes }} </span>
    <span v-if="items.observacaoInstrutor">Observações: {{ items.observacaoInstrutor }}</span>
  </v-card-text>
</template>
<script>
export default {
  props: ["items"],
  data() {
    return {
      headers: [
        {
          text: "Nome",
          align: "start",
          sortable: false,
          value: "nomeExercicio"
        },
        {
          text: "Séries",
          align: "start",
          sortable: false,
          value: "quantidadeDeSeries"
        },
        {
          text: "Reps",
          align: "start",
          sortable: false,
          value: "quantidadeDeRepeticoes"
        }
      ]
    };
  }
}
</script>

<style scoped>

  div{
    color: white;
    background-color: #5c3551ff;
  }

</style>