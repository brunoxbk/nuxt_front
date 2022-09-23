<template>
    <v-row justify="center" align="center">
      <v-col  cols="12" sm="8" md="6">
        <v-card class="elevation-12">
            <v-toolbar dark color="primary">
                <v-toolbar-title>Login form</v-toolbar-title>
            </v-toolbar>
            <v-card-text>
                <v-form>
                    <v-text-field
                        v-model="username"
                        prepend-icon="mdi-account"
                        name="username"
                        label="Login"
                        type="text"
                    ></v-text-field>
                    <v-text-field
                        id="password"    
                        v-model="password"    
                        prepend-icon="mdi-lock"
                        name="password"
                        label="Password"
                        type="password"
                    ></v-text-field>
                </v-form>
            </v-card-text>
            <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="primary"  @click="login">Login</v-btn>
            </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
</template>
  
  <script>
  export default {
    name: 'LoginPage',
    data() {
        return {
            username: 'uuu',
            password: 'xxx'
        }
    },
    methods: {
        async login() {
            await this.$axios.$post('http://localhost:3000/auth/sign_in', { 'username': this.username, 'password': this.password })
                .then(function (response) {
                    console.log(response);
                });
        },
        async loginGov() {
            //  https://sso.staging.acesso.gov.br/authorize?response_type=code&client_id=ec4318d6-f797-4d65-b4f7-39a33bf4d544&scope=openid+email+profile&redirect_uri=http%3A%2F%2Fappcliente.com.br%2Fphpcliente%2Floginecidadao.Php&nonce=3ed8657fd74c&state=358578ce6728b%
            await this.$axios.$post('http://localhost:8080/login', { 'username': this.username, 'password': this.password })
                .then(function (response) {
                    console.log(response);
                });
        }

    }
  }
  </script>
  