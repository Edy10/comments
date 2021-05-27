<template>
    <div>
        <div v-for="(msg, index) in pensamentos" :key="index" class="comentarios">
            <v-card class="mx-auto" dark >
                <v-system-bar>
                    <v-spacer></v-spacer>
                    <v-icon class="fechar" @click="apagarComentario(index)">mdi-close</v-icon>
                </v-system-bar>
                <v-card-text class="headline font-weight-bold">
                    "{{msg.desc}}"
                </v-card-text>
                <v-card-actions>
                    <v-list-item class="grow">
                        <v-list-item-avatar color="grey darken-3" class="autor">
                        <v-img class="elevation-6" alt="" src="https://avataaars.io/?avatarStyle=Transparent&topType=ShortHairShortCurly&accessoriesType=Prescription02&hairColor=Black&facialHairType=Blank&clotheType=Hoodie&clotheColor=White&eyeType=Default&eyebrowType=DefaultNatural&mouthType=Default&skinColor=Light" ></v-img>
                        </v-list-item-avatar>

                        <v-list-item-content>
                        <v-list-item-title>{{msg.nome}}</v-list-item-title>
                        </v-list-item-content>

                        <v-row align="center" justify="end">
                            <v-btn class="ma-2" text icon color="blue lighten-2" @click="curti(index, 'P')">
                                <span class="subheading mr-2">{{msg.qtdCurtidasP}}</span> <v-icon>mdi-thumb-up</v-icon>
                            </v-btn>

                            <v-btn class="ma-2" text icon color="red lighten-2" @click="curti(index, 'N')">
                               <span class="subheading mr-2">{{msg.qtdCurtidasN}}</span> <v-icon>mdi-thumb-down</v-icon>
                            </v-btn>
                        </v-row>
                    </v-list-item>
                </v-card-actions>
            </v-card>
        </div>
    </div>
</template>

<script>
export default {
    props: ['coment'],
    methods:{
        apagarComentario(id){
            this.coment.splice(id, 1);
        },
        curti(id, status){
            this.coment.forEach((value, key) => {
                if(id == key){
                    if(status === 'P'){
                        value.qtdCurtidasP = value.qtdCurtidasP + 1;
                    }else{
                        value.qtdCurtidasN = value.qtdCurtidasN + 1;
                    }
                }
            });
        }
    },
    computed:{
        pensamentos(){
            return this.coment.map(coments => ({
                ...coments,
                nome: coments.nome.trim() == '' ? 'Anônimo' : coments.nome
            }))
        }
    },
    watch:{
        coment(val){
            console.log(val);
        }
    }
}
</script>

<style scoped>
    .comentarios{
        margin-top: 20px;
        padding: 30px;
    }
    .fechar{
        cursor: pointer!important;
    }
    .fechar{
        margin-top: 1px;
        color: white;
        padding: 5px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 12px;
    }
</style>
