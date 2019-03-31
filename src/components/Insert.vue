<template>
    <div class="add-tarefa">
        
        <input @keydown.enter="addTarefa" type="text" placeholder="Insira uma tarefa" v-model="nome">
        <button @click="addTarefa">+</button>
    </div>
</template>

<script>
export default {

    data() {
        return {

            nome: ''
        }
    },

    methods: {

        addTarefa() {

            if (this.nome.length > 0) {

                this.$emit('addTarefas', {nome: this.nome});
                this.nome = '';
            }
        }
    },
}
</script>

<style scoped>

    .add-tarefa h1 {
        text-align: center;
    }
    
    .add-tarefa input {
        width: 30vw;
        height: 30px;
        padding: 10px 10px;
        font-weight: 600;
        font-size: 1.3rem;
        border-top-left-radius: 10px;
        border-bottom-left-radius: 10px;
        outline: none;
        color: #666;
    }

    .add-tarefa button {
        width: 40px;
        height: 54px;
        padding: 10px 10px;
        font-weight: 600;
        font-size: 1.3rem;
        border-top-right-radius: 10px;
        border-bottom-right-radius: 10px;
        outline: none;
        color: #FFF;
        background-color: rgb(25, 81, 85);
    }
</style>
