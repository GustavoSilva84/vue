<template>
    
    <form v-on:submit="enviar($event)">

        <div class="input-group mb-3">

            <input v-model="msg" type="text" class="form-control" placeholder="Usuario" aria-label="Recipient's username" aria-describedby="button-addon2">

            <div class="input-group-append">
                <button class="btn btn-outline-secondary" type="submit" id="button-addon2"> Enviar </button>
            </div>

        </div>
        
        <div id="chat">

            <li v-for="(msgs, indice) in chat" v-bind:key="msgs.msg"> 
                {{ msgs.msg }} <strong id="apagar" v-on:click="deletar(indice)"> excluir </strong>
            </li>

        </div>

    </form>

</template>enviar arquivo para o backend com node js


<script>

export default {

    name: 'rr',
 
    data() {

        return {
            msg: '',
            chat: [], 
            indice: ''
        }

    },
    
    methods: {

        enviar(event) {

            event.preventDefault();
            if(this.msg.trim() == '') return;

            this.chat.push({msg: this.msg});
            this.msg = ''

        },

        deletar(indice) {
            return this.chat.splice(indice, 1)
        }
    },

    computed: {

        mostraMsg() {
            console.log(localStorage.getItem('chat'))
            return localStorage.getItem('chat')
        },

    }

}

</script>

<style>

    .input-group {
        width: 400px;
        margin: 0 auto;
    }

    #apagar {
        color: rgb(66, 66, 253);
        cursor: pointer;
        
    }

</style>