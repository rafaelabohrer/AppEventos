<template>
  <v-card
  class="mx-auto"
  >
  <div class="text-center">
    <v-card-title>Bem-vindo!</v-card-title>
    <v-divider></v-divider>
    <v-card-text>Utilize nosso sistema de gestão de eventos, e facilite a organização de sua agenda</v-card-text>
    <v-btn color="pink-lighten-3" variant="outlined" to="/cadastro">Cadastre seu Evento</v-btn>
    <v-card-text>Cadastre seu primeiro evento clicando no botão acima!</v-card-text>
  </div>
  </v-card>
  
<v-divider></v-divider>

<v-row>

<v-col order="1">
  <v-card color="green-lighten-3" height="130">
    <v-card-title>Quem somos?</v-card-title>
    <v-card-subtitle>Conheça nossa organização</v-card-subtitle>
    <div class="text-center">
      <v-btn color="light-green-darken-3" to="/sobre">Saiba Mais</v-btn>
    </div>
  </v-card>
</v-col>



  <v-col order="12">
  <v-card color="yellow-lighten-1" height="130">
    <v-card-title>Contate-nos</v-card-title>
    <v-card-subtitle>Precisando de suporte?</v-card-subtitle>
    <div class="text-center">
      <v-btn color="yellow-darken-4" to="/contato">Contato</v-btn>
    </div>
  </v-card>
</v-col>

</v-row>

</template>

<script setup>
import Cadastro from './cadastro.vue';

  //
</script>
