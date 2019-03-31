<template>
    <div class="tarefas-grid">

        <template v-if="tarefas.length">
        
                <Tarefas v-for="(tarefa, i) in tarefas" 
                    :key="tarefa.nome" 
                    :tarefaObj="tarefa"
                    @removeTarefa="$emit('deletar', i)">

                </Tarefas>
            
        </template>
        
        <span class="sem-tarefas" v-else>Sua vida está em dia :)</span>

    </div>
</template>

<script>
import Tarefas from './Tarefas.vue';
export default {

    components: {
        Tarefas,
    },

    props: {

        tarefas: {
            type: Array,
            required: true,
        }
    },
}
</script>

<style>
    .tarefas-grid {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;
        
    }

    .sem-tarefas{
        font-size: 1.3rem;
        margin-top: 30px;
        color: #ddd;
    }
</style>
