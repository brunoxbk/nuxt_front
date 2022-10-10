<template>
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="6">
        <v-card class="logo py-4 d-flex justify-center">
          <NuxtLogo />
          <VuetifyLogo />
        </v-card>
        <v-card class="logo py-4 d-flex justify-center">
          <PostForm :send="sendMessage" />
        </v-card>
        <v-card>
          <v-card-title class="headline">
           Posts
          </v-card-title>
          <v-card-text>
            <v-list >
              
                
                <v-list-item two-line v-for="item in posts" :key="item.id">
                    <v-list-item-content>
                    <v-list-item-title>{{item.text}}</v-list-item-title>
                    <v-list-item-subtitle>{{item.user_name}}</v-list-item-subtitle>
                    <v-list-item-subtitle>{{item.created}}</v-list-item-subtitle>
                    
                    </v-list-item-content>
                </v-list-item>
              
              
              </v-list>
            
          </v-card-text>
          <v-card-actions>
            <v-spacer />
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
        components: { PostForm },
        mounted(){
          console.log(this.$auth.strategy.token.get())
          this.fetchPosts()
        },
        data() {
          return {
            posts: [],
          }
      },
        methods: {
          async sendMessage(message) {
            try {
              const post = await this.$axios.$post('/posts', {user_id: this.$auth.user.id, text: message, created: new Date().toISOString()});
              console.log(post);
            } catch (err) {
                console.log(err)
            }

            this.fetchPosts()
          },

          async fetchPosts() {
             const result = await this.$axios.$get('/posts');

             console.log(result);

             this.posts = result
          }
        },
    }
  </script>
  