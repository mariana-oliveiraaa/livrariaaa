<script>
import { v4 as uuid } from "uuid";
export default {
  data() {
    return {
      novo_editora: "",
      novo_Rede_Social: "",
      editoras: [
        {
          id: "9a7c7c02-874d-4556-8a13-4a33c56571d1",
          name: "Darkside Books",
          Rede_Social: "@Darksidebooks",
        },
        {
          id: "475f6d39-5a56-4442-8a2d-5ceba6b4b807",
          name: "Aleph",
          Rede_Social: "@Aleph_editions",
        },
        {
          id: "874b37b6-3546-4c05-bc54-5d0fdb886d16",
          name: "Suma",
          Rede_Social: "@Editorasuma",
        },
        {
          id: "9b35ce67-a4ec-45a0-be67-1983e37bd723",
          name: "Editorial Record",
          Rede_Social: "@Editorarecord",
        },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.novo_editora !== "") {
        const novo_id = uuid();
        this.editoras.push({
          id: novo_id,
          name: this.novo_editora,
          Rede_Social: this.novo_Rede_Social,
        });
        this.novo_Rede_Social = "";
        this.novo_editora = "";
      }
    },
    excluir(editora) {
      const indice = this.editoras.indexOf(editora);
      this.editoras.splice(indice, 1);
    },
  },
};
</script>
<template>
  <div class="container">
    <div class="title">
      <h2>Editora</h2>
    </div>
    <div class="form-input">
      <input
        type="text"
        placeholder="Nome"
        v-model="novo_editora"
        @keypress.enter="salvar"
      />
       <input
        type="text"
        placeholder="Rede Social"
        v-model="novo_Rede_Social"
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
            <th>Rede Social</th>
            <th>Ação</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="editora in editoras" :key="editora.id">
            <td>{{ editora.id }}</td>
            <td>{{ editora.name }}</td>
            <td>{{ editora.Rede_Social }}</td>
            <td>
              <button @click="excluir(editora)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<style></style>
