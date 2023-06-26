<template>
  <div class="flex flex-col items-center pt-20">
    <div class="flex items-center">
      <input
        type="text"
        class="w-96 h-12 text-2xl"
        v-model="tarefa"
        @keypress.enter="adicionarLista"
      />
      <button class="bg-blue-700 text-4xl p-1" @click.prevent="adicionarLista">
        +
      </button>
    </div>
    <div class="pt-12">
      <ul class="flex flex-col gap-4 w-96">
        <li
          v-for="tarefa in tarefas"
          :key="tarefa.message"
          class="flex justify-between bg-white p-2 rounded-lg"
        >
          <p :class="{ ativo: tarefa.isDone }">{{ tarefa.message }}</p>
          <div class="flex items-center gap-1">
            <button @click="tarefa.isDone = !tarefa.isDone">
              <img src="../assets/check.png" width="20" alt="check" />
            </button>
            |
            <button @click="removerTarefa(tarefa)">
              <img src="../assets/trash.png" width="20" alt="trash" />
            </button>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tarefas: [],
      tarefa: "",
    };
  },
  methods: {
    adicionarLista() {
      if (this.tarefa != "") {
        this.tarefas.push({ message: this.tarefa, isDone: false });
        this.tarefa = "";
      }
    },
    removerTarefa(task) {
      this.tarefas.splice(this.tarefas.indexOf(task), 1);
      console.log(task);
    },
    checarTarefa() {},
  },
};
</script>

<style>
.ativo {
  text-decoration: line-through;
}
</style>
