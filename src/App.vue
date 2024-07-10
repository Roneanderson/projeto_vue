<script setup>
    import { reactive } from 'vue';
    import Cabecalho from './components/Cabecalho.vue';
    import Formulario from './components/Formulario.vue';

const estado = reactive({
    tarefa: {
        numero1: 0,
        numero2: 0,
        resultado: 0,
        operador: 'somar',
    }
})

//função acessando valor do campo1
function getNumeroCampo(evento) {
    estado.tarefa.numero1 = parseFloat(evento.target.value) || 0;
    getOperacao();
}

//função acessando valor do campo2
function  getNumeroCampo2(evento) {
    estado.tarefa.numero2 = parseFloat(evento.target.value) || 0;
    getOperacao();
}

//estado da operação de calcular
const getOperacao  = () => {
    switch (estado.tarefa.operador) {
        case 'adicao':
            estado.tarefa.resultado = estado.tarefa.numero1 + estado.tarefa.numero2;
            break;
        case 'subtracao':
            estado.tarefa.resultado = estado.tarefa.numero1 - estado.tarefa.numero2;
            break;
        case 'multiplicacao':
            estado.tarefa.resultado = estado.tarefa.numero1 * estado.tarefa.numero2;
            break;
        case 'divisao':
            estado.tarefa.resultado = estado.tarefa.numero1 / estado.tarefa.numero2;
            break;
            
    }
}
</script>

<template>
    <div class="container">
        <Cabecalho/>
        <Formulario :get-numero-campo="getNumeroCampo" :get-numero-campo2="getNumeroCampo2" :operador="evento => estado.tarefa.operador = evento.target.value" :resultado="estado.tarefa.resultado"/>
    </div>
</template>

