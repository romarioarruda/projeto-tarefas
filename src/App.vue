<template>
    <div class="app">
        <h1>Tarefas</h1>

        <template v-if="listaTarefas.length">
            <Progress :progresso="progresso"/>
        </template>

        <Insert @addTarefas="addTarefa" />

        <TarefasGrid :tarefas="listaTarefas" @deletar="deletaTarefa" />

    </div>
</template>

<script>
import Progress from './components/Progress.vue';
import Insert from './components/Insert.vue';
import TarefasGrid from './components/TarefasGrid.vue';
export default {

    components: {
        Progress,
        Insert,
        TarefasGrid,
    },

    data() {

        return {

            listaTarefas: [],
        }
    },

    computed: {
        progresso() {

            const total = this.listaTarefas.length;
            const feita = this.listaTarefas.filter(t => !t.pendente).length;

            return Math.round(feita / total * 100) || 0;
            
        }
    },

    watch: {

        listaTarefas: {

            deep: true,
            handler() {

                localStorage.setItem('tarefas', JSON.stringify(this.listaTarefas));
            }
        }
    },

    methods: {

        addTarefa(tarefa) {
            const verificaNome = t => t.nome === tarefa.nome;
            const nomeValido = this.listaTarefas.filter(verificaNome).length == 0;

            if (nomeValido) {

                this.listaTarefas.push({
                    nome: tarefa.nome,
                    pendente: tarefa.pendente || true,
                });
            }
        },

        deletaTarefa(i) {
            this.listaTarefas.splice(i, 1);
        }
    },

    created() {
        const json = localStorage.getItem('tarefas');
        const array = JSON.parse(json);
        this.listaTarefas = Array.isArray(array) ? array : [];
    },

}
</script>

<style>

body {
    background: linear-gradient(to right, rgb(16, 64, 83), rgb(26, 44, 61));
    font-family: 'Lato', sans-serif;
    color: #FFF;
}

.app{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    flex-direction: column;
    height: 60vh;
}

</style>
