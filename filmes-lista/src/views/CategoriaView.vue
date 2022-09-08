<script>
import { v4 as uuid } from "uuid";
export default {
  data() {
    return {
      novo_categoria: "",
      Categoria: [
        {
          id: "9a7c7c02-874d-4556-8a13-4a33c56571d1",
          name: "Machado de Assis categoria",
        },
        {
          id: "475f6d39-5a56-4442-8a2d-5ceba6b4b807",
          name: "Jorge Amado",
        },
        {
          id: "874b37b6-3546-4c05-bc54-5d0fdb886d16",
          name: "Monteiro Lobato",
        },
        {
          id: "9b35ce67-a4ec-45a0-be67-1983e37bd723",
          name: "Fernando Pessoa",
         
        },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.novo_categoria !== "") {
        const novo_id = uuid();
        this.Categoria.push({
          id: novo_id,
          name: this.novo_categoria,
        });
        this.novo_categoria = "";
      }
    },
    excluir(Categoria) {
      const indice = this.Categoria.indexOf(this.Categoria);
      this.Categoria.splice(indice, 1);
    },
  },
};
</script>
<template>
  <div class="container">
    <div class="title">
      <h2>Categoria</h2>
    </div>
    <div class="form-input">
      <input
        type="text"
        placeholder="Nome"
        v-model="novo_categoria"
        @keypress.enter="salvar"
      />

      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-items">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>Ação</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="Categoria in Categoria" :key="Categoria.id">
            <td>{{ Categoria.id }}</td>
            <td>{{ Categoria.name }}</td>
            <td>
              <button @click="excluir(Categoria)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<style></style>
