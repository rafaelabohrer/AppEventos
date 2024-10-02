<template>
  <v-app id="inspire">
    <v-app-bar class="px-3" density="compact" flat>
      <v-avatar class="hidden-md-and-up" color="grey-darken-3" size="32"></v-avatar>

      <v-spacer></v-spacer>

      <v-tabs color="pink-lighten-3" centered>
        <v-tab text="Início" to="/" />
        <v-tab text="Gerenciar Eventos" to="/cadastro" />
        <v-tab text="Sobre Nós" to="/sobre"/>
        <v-tab text="Contato" to="/contato"/>
      </v-tabs>
      <v-spacer></v-spacer>
    </v-app-bar>

    <v-main class="bg-pink-lighten-4">
      <v-container>
        <v-row>
          <v-col cols="12">
            <v-sheet min-height="70vh" rounded="lg">
              <v-container>
                <router-view />
              </v-container>
            </v-sheet>
          </v-col>

        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>
