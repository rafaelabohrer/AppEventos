<template>
  <v-card>
    <v-card-title>Cadastro de Eventos</v-card-title>
    <v-card-text>Insira as informações do Evento:</v-card-text>

    <v-container>
      <v-form ref="form">
        <v-text-field v-model="formData.nomeevento" label="Nome do Evento"></v-text-field>
        <v-text-field v-model="formData.localevento" label="Local do Evento"></v-text-field>
        <v-textarea v-model="formData.descricaoevento" label="Descrição"></v-textarea>
        <v-text-field v-model="formData.dataevento" label="Data do Evento" type="date"></v-text-field>

        <v-card-actions>
          <v-btn type="button" @click="submitForm" variant="outlined" color="pink-lighten-3">
            {{ editIndex !== null ? 'Atualizar' : 'Cadastrar' }}
          </v-btn>
        </v-card-actions>
      </v-form>
    </v-container>

    <v-divider></v-divider>

    <v-container>
      <v-card-title>Lista de Eventos</v-card-title>
      <v-card v-for="(item, index) in items" :key="index" class="my-2">
        <v-card-title @click="item.showDetails = !item.showDetails">
          {{ item.nomeevento }}
          <v-icon>{{ item.showDetails ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
        </v-card-title>
        <v-card-text v-show="item.showDetails">
          <div>Local: {{ item.localevento }}</div>
          <div>Data: {{ item.dataevento }}</div>
          <div>Descrição: {{ item.descricaoevento }}</div>

          <v-divider></v-divider>
          <v-card-text>Adicione um convidado:</v-card-text>
          <v-text-field v-model="newGuest" label="Nome do convidado" @keyup.enter="addGuest(item)"></v-text-field>
          <v-list>
            <v-list-item-group>
              <v-list-item v-for="(guest, guestIndex) in item.convidados" :key="guestIndex">
                <v-card-text>Lista de Convidados:</v-card-text>
                <v-list-item-content>
                  <v-list-item-title>{{ guest }}</v-list-item-title>
                </v-list-item-content>
                <v-list-item-action>
                  <v-btn @click="editGuest(item, guestIndex)" color="pink-lighten-3" variant="outlined">Alterar</v-btn>
                  <v-btn @click="removeGuest(item, guestIndex)" color="pink" variant="outlined">Remover</v-btn>
                </v-list-item-action>
              </v-list-item>
            </v-list-item-group>
          </v-list>
          <v-btn @click="editEvent(index)" color="cyan-lighten-1">Editar Evento</v-btn>
          <v-btn @click="deleteEvent(index)" color="deep-purple-darken-3">Excluir Evento</v-btn>
        </v-card-text>
      </v-card>
    </v-container>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      formData: {
        nomeevento: '',
        localevento: '',
        dataevento: '',
        descricaoevento: '',
        convidados: [] // Lista de convidados para cada evento
      },
      items: [],
      editIndex: null,
      newGuest: '', // Para adicionar um novo convidado
    };
  },
  methods: {
    submitForm() {
      if (this.editIndex !== null) {
        this.items[this.editIndex] = { ...this.formData, showDetails: false };
        this.editIndex = null;
      } else {
        const newEvent = { ...this.formData, showDetails: false, convidados: [] };
        this.items.push(newEvent);
      }
      this.resetForm();
    },
    addGuest(event) {
      if (this.newGuest.trim()) {
        event.convidados.push(this.newGuest.trim());
        this.newGuest = ''; // Limpa o campo de convidado
      }
    },
    editGuest(event, guestIndex) {
      const editedGuest = prompt("Editar Convidado:", event.convidados[guestIndex]);
      if (editedGuest) {
        event.convidados[guestIndex] = editedGuest.trim();
      }
    },
    removeGuest(event, guestIndex) {
      event.convidados.splice(guestIndex, 1);
    },
    editEvent(index) {
      this.formData = { ...this.items[index] };
      this.editIndex = index;
    },
    deleteEvent(index) {
      this.items.splice(index, 1);
    },
    resetForm() {
      this.formData = { nomeevento: '', localevento: '', dataevento: '', descricaoevento: '', convidados: [] };
      this.newGuest = ''; // Limpa o campo de convidado
    }
  }
};
</script>
