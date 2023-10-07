<template>
   <v-main class="grey lighten-3">
      <v-container>
        <v-row>
          <v-col>
            <v-sheet color="grey lighten-3" class="my-5" rounded="lg">
              <v-card class="mx-auto"  max-width="456" outlined>
                <v-list-item three-line>
                  <v-list-item-content>
                    <div class="text-overline mb-4">Fazer nova publicação</div>
                    <v-text-field
                        v-model="textInput"
                        @keyup.enter="addPost"
                        height="70"
                        hide-details
                        label = "Digite aqui"
                    ></v-text-field>
                  </v-list-item-content>
                </v-list-item>

                <v-card-actions class="justify-end">
                  <v-btn @click="addPost"> 
                    <v-icon color="blue darken-2" >mdi-send</v-icon>
                  </v-btn>
                </v-card-actions>
                </v-card>

                <div class="list-group-item" v-for="(post, index) in posts" :key="index">
                    <v-card outlined class="mx-15, my-5" color="grey lighten-2" accent-4 >           
                        <v-card-subtitle class="font-weight-bold">{{ post.name }}</v-card-subtitle>
                        <v-card-text>{{ post.text }}</v-card-text>
                        
                        <delPostComponent :post="post" @excluirMensagem="excluirMensagem(post)"></delPostComponent>
                            
                       
                    </v-card>
                </div>
            </v-sheet>
          </v-col>
        </v-row>
      </v-container>
    </v-main> 
</template>

<script>
import delPostComponent from './delPostComponent.vue';

    export default {
        name: 'postComponent',
        components: {
          delPostComponent
        },
      
        data() {
            return{
                textInput: '',
                posts: [
                  
                ]
        }
        },
        methods: {
            addPost(){
                this.posts.push({
                    name: 'Beyond User',
                    text: this.textInput
                })
                this.textInput = ''
            },
            excluirMensagem(post){
              const index = this.posts.indexOf(post);
              if (index > -1) {
                this.posts.splice(index, 1);
              }    
            }
        }
    }
</script>


