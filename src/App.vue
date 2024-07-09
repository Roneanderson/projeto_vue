<script setup>
import { reactive } from 'vue';

const estado = reactive({
    tarefa: {
        numero1: 0,
        numero2: 0,
        resultado: 0,
        operador: 'somar',
    }
})

//função acessando valor do campo1
function getnumeroCampo(evento) {
    estado.tarefa.numero1 = parseFloat(evento.target.value) || 0;
    getOperacao();
}

//função acessando valor do campo2
function  getnumeroCampo2(evento) {
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
        <form>
            <div class="row">
                <div class="col">
                    <input type="number" @change="getnumeroCampo" placeholder="Digite o valor 1">
                </div>
                <div class="col-md-3">
                    <ul>
                        <select @change="evento => estado.tarefa.operador = evento.target.value" class="col-md-3 p-md-1">
                            <option value="adicao">+</option>
                            <option value="subtracao">-</option>
                            <option value="multiplicacao">*</option>
                            <option value="divisao">/</option>
                        </select>
                    </ul>
                </div>
                <div class="col">
                    <input type="number" @change="getnumeroCampo2" placeholder="Digite valor 2">
                </div>
            </div>
        </form>
        <ul class="list-group mt-4">
            <li class="list-group-item">
                Resultado: {{ estado.tarefa.resultado }}
            </li>
        </ul>
    </div>
</template>

<style scoped>
.done {
    text-decoration: line-through;
}
</style>