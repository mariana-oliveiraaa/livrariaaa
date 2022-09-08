<script>
import { v4 as uuid } from "uuid";
export default {
  data() {
    return {
      novo_autor: "",
      novo_editora: "",
      novo_categoria: "",
      novo_livro: "",
      livros: [
        {
          id: "98940c1e-e312-4f81-801b-ec969b2e6ed4",
          name: "A Cartomante",
          autor: "Machado de Asis ",
          editoraid: "o Companhia das Letras.",
          categoria: "Realismo",
        },
        {
          id: "3f8e15ef-cf81-4596-9f02-e51a6a9b38a3",
          name: "Capitães de Areia",
          autor: "Jorge Amado",
          editoraid: "Festa",
          categoria: "Modernismo",
        },
        {
          id: "2be66caf-d783-426e-8723-55f518c06a6f",
          name: "Fábulas",
          autor: "Monteiro Lobato",
          editoraid: "Companhia Editora Nacional",
          categoria: "literatura infantil",
        },
        {
          id: "9a7c7c02-874d-4556-8a13-4a33c56571d1",
          name: "O marinheiro",
          autor: "Fernando Pessoa",
          editoraid: "Der Audio Verlag",
          categoria: "Pop",
        },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.novo_livro !== "") {
        const novo_id = uuid();
        this.livros.push({
          id: novo_id,
          name: this.novo_livro,
          autor: this.novo_autor,
          editoraid: this.novo_editora,
          categoria: this.novo_categoria,
        });
        this.novo_livro = "";
        this.novo_autor = "";
        this.novo_editora = "";
        this.novo_categoria = "";
      }
    },

    excluir(livro) {
      const indice = this.livros.indexOf(livro);
      this.livros.splice(indice, 1);
    },
  },
};
</script>
<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de Livros</h2>
    </div>
    <div class="form-input">
      <input
        type="text"
        placeholder="Nome"
        v-model="novo_livro"
        @keypress.enter="salvar"
      />
      <input
        type="text"
        placeholder="Autor"
        v-model="novo_autor"
        @keypress.enter="salvar"
      />
      <input
        type="text"
        placeholder="Editora"
        v-model="novo_Editora"
        @keypress.enter="salvar"
      />
      <input
        type="text"
        placeholder="Categoria"
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
            <th>Autor</th>
            <th>Editora</th>
            <th>Categoria</th>
            <th>Nome</th>
            <th>Ação</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="livro in livros" :key="livro.id">
            <td>{{ livro.id }}</td>
            <td>{{ livro.autor }}</td>
            <td>{{ livro.editoraid }}</td>
            <td>{{ livro.categoria }}</td>
            <td>{{ livro.name }}</td>
            <td>
              <button @click="excluir(livro)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style></style>
