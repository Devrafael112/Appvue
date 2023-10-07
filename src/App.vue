<template>
  <v-app id="inspire">
    <v-app-bar app color="blue darken-2" flat>
      <v-container class="py-0 fill-height">
        <v-icon class="mr-10" size="45" color="white">mdi-account</v-icon>

        <v-btn
          v-for="link in links"
          :key="link"
          text
          color="white"
          justify-self=""
        >
          {{ link }}
        </v-btn>
        <v-spacer></v-spacer>
        <delAllPostComponent @deletar-todas-mensagens="deleteAllPost"></delAllPostComponent>
      </v-container>
    </v-app-bar>
    <post-component></post-component>
  </v-app>
</template>

<script>
import postComponent from './components/postComponent.vue';
export default {
  components: { postComponent},
  data: () => ({
    links: ["Página inicial", "Mensagens", "Perfil"],
    components: {
      postComponent,
    }
    
  }),
};
</script>