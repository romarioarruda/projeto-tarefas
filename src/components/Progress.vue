<template>
    <div class="barra-progresso">

        <span class="value">{{ progresso }} %</span>

        <div class="progresso" :style="{width: progresso+'%'}"></div>
    </div>
</template>

<script>
export default {

    props: {
        progresso: {
            type: Number,
            default: 0,
        }
    }
}
</script>

<style>

    .barra-progresso{
        position: relative;
        border: 1px solid #FFF;
        width: 80%;
        border-radius: 8px;
        margin-bottom: 20px;
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .progresso {
        position: absolute;
        border-radius: 8px;
        background-color: rgb(60, 156, 68);
        height: 100%;
        align-self: flex-start;
        
    }

    .value {
        z-index: 1;
        font-weight: 700;
    }
    
</style>
