<template>
    
    <form v-on:submit="enviar(event)">

        <input type="text" v-model="msg">
        <button type="submit"> Enviar </button>
        <li v-for="dados in chat" v-bind:key="dados.msg">
            {{ dados.msg }}
        </li>

    </form>

</template>


<script>

export default {

    name: 'Teste',
 
    data() {

        return {
            msg: '',
            chat: []
        }

    },
    
    methods: {

        enviar(event) {
            event.pre
            if(this.msg.trim() == '') return;
            this.chat.push({msg: this.msg});
        }

    },

    computed: {

        mostraMsg() {
            return this.chat;
        }

    }

}

</script>
