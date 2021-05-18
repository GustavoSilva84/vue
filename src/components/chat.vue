<template>
    
    <form v-on:submit="Enviar($event)">

        <div class="input-group mb-3">

            <input v-model="msg" type="text" class="form-control" placeholder="Usuario" aria-label="Recipient's username" aria-describedby="button-addon2">

            <div class="input-group-append">
                <button class="btn btn-outline-secondary" type="submit" id="button-addon2"> Enviar </button>
            </div>

        </div>
        
        <div id="chat">

            <ul>
                <li v-for="(msgs, indice) in MostraMsg" v-bind:key="msgs.msg"> 
                    {{ msgs.msg }} <strong id="apagar" v-on:click="Deletar(indice)"> excluir </strong>
                </li>
            </ul>

        </div>

    </form>

</template>

<script>

    export default {

        name: 'Chat',
    
        data() {

            return {
                msg: '',
                chat: [],
                indice: ''
            }

        },
        
        methods: {

            Enviar(event) {

                event.preventDefault();
                if(this.msg.trim() == '') return;

                this.chat.push({msg: this.msg});

                this.chat.forEach(element => {
                    console.log(element.msg)
                });

                this.msg = ''

            },

            Deletar(indice) {
                return this.chat.splice(indice, 1)
            }

        },

        computed: {

            MostraMsg() {
                return this.chat
            }

        }

    }

</script>

<style>

    ul {
        list-style: none;
    }

    .input-group {
        width: 400px;
        margin: 0 auto;
    }

    #apagar {
        color: rgb(66, 66, 253);
        cursor: pointer;
        
    }

</style>