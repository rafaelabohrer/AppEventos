<template>
    <v-card
    class="mx-auto"
    >
    <div class="text-center">
      <v-card-title>Contato</v-card-title>
      <v-divider></v-divider>
      <v-card-text>Entraremos em contato por e-mail, no momento do recebimento do suporte (é mentira)</v-card-text>
    </div>
    </v-card>
    
    <v-container>
        <v-text-field label="Nome Completo"></v-text-field>
        <v-text-field label="E-mail"></v-text-field>
        <v-textarea label="Conte-nos sobre sua experiência"></v-textarea>
        <v-btn variant="outlined" color="pink-lighten-3">Enviar</v-btn>
    </v-container>

  </template>
  
  <script setup>
  
    //
  </script>