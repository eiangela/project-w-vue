<template>
    <button @click="disparaAcao()" class="botao botao-padrao" type="tipo">{{ rotulo }}</button>

</template>

<script>
export default {
    props: {
       tipo: {
           type: String, 
           required: true
       },

       rotulo: {
           type: String, 
           required: true
       },

       confirmacao: Boolean,
       estilo: String
    },

    methods: {
        disparaAcao() {
            if (this.confirmacao) {
                if (confirm('Confrma operação?')) {
                    this.$emit('botaoAtivado');
                }
                return;
            }

            this.$emit('botaoAtivado')
        }
    },
    computed: {
        estiloDoBotao() {

            // se o valor é padrão ou não passou nada para estilo
            if (this.estilo == 'padrao' || !this.estilo) return 'botao botao-padrao';

            if (this.estilo == 'perigo') return 'botao botao-perigo';
        }
    }
}

</script>

<style>
.botao {
    display: inline-block;
    padding: 10px;
    border-radius: 3px;
    margin: 10px;
    font-size: 1.2em;

}

.botao-perigo {
    background: firebrick;
    color: white;
}

.botao-padrao {
    background: darkcyan;
    color: white;
}
</style>