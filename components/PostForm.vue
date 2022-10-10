<template>
    <v-container fluid>
      <v-form
        ref="form"
        v-model="valid"
        lazy-validation
      >
        
        <v-textarea
              solo
              name="input-7-4"
              label="Post"
              v-model="message"
              :rules="messageRules"
              required
            ></v-textarea>

        <v-btn class="mr-4" @click="submit()">
          submit
        </v-btn>
      </v-form>
    </v-container>
  </template>
   <script>
   
    export default {
      name: 'PostForm',
      data() {
        return {
          valid: false,
          message: '',
          messageRules: [
            v => !!v || 'Post é requerido',
          ]
        }
      },
      mounted(){
        // this.send('aaaaaa')
      },
      methods: {
        validate () {
          this.$refs.form.validate()
        },
        submit(){
          if (this.$refs.form.validate()) {
            this.send(this.message);
            this.reset()
          }
        },
        reset () {
          this.$refs.form.reset()
        },
        resetValidation () {
          this.$refs.form.resetValidation()
        },
      },

      props: {
        send: { type: Function },
      },
    }
</script>