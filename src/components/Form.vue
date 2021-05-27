<template>
  <v-container>
    <v-card class="form">
      <h1>COMENTÁRIOS E POSTS</h1>
      <v-spacer></v-spacer>
        <v-form>
            <v-text-field v-model="comentario.nome" label="Name">
            </v-text-field>

            <v-textarea v-model="comentario.desc" label="Comentário" rows="3">
            </v-textarea>

            <v-btn color="success" class="mr-4" @click="cadastrar()" :disabled="!comentario.desc">
                Comentar
            </v-btn>
        </v-form>
    </v-card>
    <v-spacer></v-spacer>
    <Comentarios :coment="comentarioOrdenados"> </Comentarios>
  </v-container>
</template>

<script>
import Comentario from "@/models/comentario";
import Comentarios from './Comentarios';
export default {
    components:{
        Comentarios
    },
    data(){
        return{
            comentario: new Comentario(),
            mensagem: []
        }
    },
    methods:{
        cadastrar(){
            this.mensagem.push(this.comentario);
            this.comentario = new Comentario();
        }
    },
    computed:{
        comentarioOrdenados(){
            return this.mensagem.sort((a,b) => (a.nome > b.nome) ? 1 : ((b.nome > a.nome) ? -1 : 0));
        }
    }
}
</script>

<style scoped>
    .form{
        padding: 30px;
    }
</style>
