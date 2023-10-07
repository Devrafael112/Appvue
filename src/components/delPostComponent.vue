<template>
    <v-btn  class="btn">
        <v-icon color="red" @click="deletarMensagem">mdi-delete</v-icon>
    </v-btn>
</template>

<script>
    export default{
        props: ['post'],
        name: 'delPostComponent',
        methods: {
            deletarMensagem(){
               this.$emit('excluirMensagem', this.post)
            }
        }
    }
</script>