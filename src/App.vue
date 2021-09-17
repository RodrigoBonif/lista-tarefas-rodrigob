<template>
<section>
  <cabecalho />
  <div class="container">
    <h2>{{ título }}</h2>
    <div class="input-group"> 
      <input @keyup.enter="adicionarTarefa" v-model="novaTarefa" type="text" />
      <span class="btn btn-primary">
        <button @click="adicionarTarefa" class="btn btn-primary"> Adicionar </button>
      </span>
    </div>


  <ul>
    <li v-for="(tarefa, index) in tarefas" :key="index" :class="{removed: tarefa.checked}">
      <input type="checkbox" v-model="tarefa.checked" class="quad" />
      <label>{{ tarefa.título  }}</label>
    </li>
  </ul>
  <footer>
     <em>Alterar Título: </em>
     <input v-model="título" type="text" />
  </footer>
</div>
</section>
</template>

<script>
import cabecalho from "@/components/cabecalho";
export default {
  name: 'App',
  components: { cabecalho },
  data() {
    return {
      título: "Minha Lista de Tarefas",
      novaTarefa: "",
      tarefas: [
      ],
    };
  },
  methods: {
    adicionarTarefa() {
      this.tarefas.push({
        título: this.novaTarefa,
        checked: false,
      });
      this.novaTarefa = "";
    },
  },
};
</script>

<style>

* {
  margin-top: 20px;
  margin-left: 0px;
  font-family: Gill Sans Extrabold, sans-serif;
  padding: 0;
}

.container {
    padding: 15px;
    background-color: #59b3cf;
    width: 40%;
    height: 100%;
    margin: 20px auto 0px auto;
    border-radius: 20px;
}

ul li {
  list-style: none;
  margin-left: 0;
  padding-left: 0;
}
.quad {
  text-align: left;
  align-itens: left;
  width: 60px;
}
h2 {
  color: #5969cf;
  text-decoration: underline;
  text-align: center;
}
button {
  margin-left: 10px;
  color: white;
  background-color: #5969cf; 
  border: none;
  width: 80px;
  height: 32px;
  border-radius: 20px
}
input {
  background-color: #88d4eb;
  color: #5969cf;
  font-size: 17px;
  width: 400px;
}
.input-group {
  text-align: center;

}
.removed {
  color: gray;
}
.removed label {
  text-decoration: line-through;
}

</style>
