<template>
    <div class="lista-tarefas">

        <div class="tarefas" :class="estadoTarefa" @click="confereTarefa">
            <span class="close" @click="$emit('removeTarefa', tarefaObj)">x</span>
            {{ tarefaObj.nome }}

        </div>

    </div>
</template>

<script>
export default {

    props: {

        tarefaObj: {
            type: Object,
            required: true,
        }
    },

    data() {

        return {

        }
    },

    computed: {
        estadoTarefa() {

            return {
                pendente: this.tarefaObj.pendente,
                feita: !this.tarefaObj.pendente,
            }
        },
        
    },

    methods: {
        confereTarefa() {

            this.tarefaObj.pendente = !this.tarefaObj.pendente;
        },

    },
}
</script>

<style scoped>

    .tarefas {
        position: relative;
        box-sizing: border-box;
        width: 350px;
        height: 50px;
        margin-right: 8px;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-top: 50px;
        
    }

    .feita {

        background-color: rgb(60, 156, 68);
        border-left: 12px solid rgb(28, 88, 33);
        text-decoration: line-through;
    }

    .pendente {
        background-color: rgb(231, 24, 59);
        border-left: 12px solid rgb(143, 22, 42);
    }

    .close {
        position: absolute;
        top: 0px;
        right: 1px;
        width: 10px;
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 5px;
        font-weight: 600;
        border-radius: 5px;
    }

    .feita .close {
        background-color: rgb(28, 88, 33);
    }

    .pendente .close {
        background-color: rgb(143, 22, 42);
    }
</style>
