<template>
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="6">
        <v-card class="logo py-4 d-flex justify-center">
          <NuxtLogo />
          <VuetifyLogo />
        </v-card>
        <v-card class="logo py-4 d-flex justify-center">
          <PostForm />
        </v-card>
        <v-card>
          <v-card-title class="headline">
           Pagina logado aa
          </v-card-title>
          <v-card-text>
            <p>
             
            </p>
            <p>
            logado: {{$auth.loggedIn}}
            </p>
            
          </v-card-text>
          <v-card-actions>
            <v-spacer />
            <v-btn color="primary" nuxt to="/inspire"> Continue </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </template>
  
  <script>
import PostForm from '~/components/PostForm.vue';
  export default {
    name: "HomePage",
    middleware: "auth",
    components: { PostForm }
}
  </script>
  