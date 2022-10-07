<template>
    <v-row justify="center" align="center">
      <v-col  cols="12" sm="8" md="6">
        <v-card class="elevation-12">
            <v-toolbar dark color="primary">
                <v-toolbar-title>Sign up form</v-toolbar-title>
            </v-toolbar>
            <v-card-text>
                <v-form>
                    <v-text-field
                        v-model="name"
                        prepend-icon="mdi-account"
                        name="name"
                        label="Nome"
                        type="text"
                    ></v-text-field>
                    <v-text-field
                        v-model="email"
                        prepend-icon="mdi-account"
                        name="email"
                        label="Email"
                        type="email"
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
                <v-btn color="primary"  @click="sign_up">Cadastrar</v-btn>
            </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
</template>
  
  <script>
  export default {
    name: 'SignUpPage',
    data() {
        return {
            email: 'uuu@gmail.com',
            password: 'xxx',
            name: 'oo'
        }
    },
    methods: {
        teste({$router}) {
            console.log(this);
            this.$router.push('/login');
        },
        async sign_up() {
            const self = this;
            await this.$axios.$post('/auth/sign_up', { 'name': this.name, 'email': this.email, 'password': this.password })
                .then(function (response) {
                    
                    self.$router.push('/login');
                });
        },
        async loginGov() {
            // https://sso.staging.acesso.gov.br/authorize?response_type=code&client_id=ec4318d6-f797-4d65-b4f7-39a33bf4d544&scope=openid+email+profile&redirect_uri=http%3A%2F%2Fappcliente.com.br%2Fphpcliente%2Floginecidadao.Php&nonce=3ed8657fd74c&state=358578ce6728b%
            await this.$axios.$post('http://localhost:3000/login', { 'name': this.name, 'password': this.password })
                .then(function (response) {
                    console.log(response);

                });
        }

    }
  }
  </script>
  