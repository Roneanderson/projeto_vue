<script setup>
import { reactive, } from 'vue';

const estado = reactive({
    tarefa: [
        {
            numero: 0,
            numero2: 0,
            resultado: 0,
            operador: 'somar',
        }
    ]
})

function getNumber() {
    console.log(estado.numero)
    if (estado.numero == '') {
        estado.numero = 0;
    }
    estado.numero = parseFloat(estado.numero)
    getOperacao()
}

function getNumber2() {
    if (estado.numero2 == '') {
        estado.numero2 = 0;
    }
    estado.numero = parseFloat(estado.numero)
    getOperacao()
}

const getOperacao = () => {
    switch(estado.operador) {
        case 'adicao':
            return estado.tarefa = (estado.numero + estado.numero2);
    }
}
</script>

<template>
    <div class="container">
        <form>
            <div class="row">
                <div class="col">
                    <input  @change="evento => getNumber = evento.target.value" type="number" placeholder="Digite valor 1 ">
                </div>
                <div class="col-md-3">
                    <ul>
                        <select @change="evento => estado.operador = evento.target.value " class="col-md-3 p-md-1">
                            <option value="adicao">+</option>
                            <option value="subtracao">-</option>
                            <option value="multiplicacao">*</option>
                            <option value="divisao">/</option>
                        </select>
                    </ul>
                </div>
                <div class="col">
                    <input @change="evento => getNumber2 = evento.target.value" type="number" placeholder="Digite valor 2">
                </div>
                
                <div class="col">
                    <input @change="evento => getOperacao = evento.target.value" type="number" placeholder="resultado">
                </div>
            </div>
        </form>
        <ul class="list-group mt-4">
            <li class="list-group-item" v-for="tarefas in estado.tarefa">
                <input :checked="tarefas.resultado" :id="tarefas.resultado" type="checkbox">
                <label :class="{done: tarefas.resultado}" class="ms-3" :for="tarefas.resultado">
                    {{ tarefas.resultado }}
                </label>
            </li>
        </ul>
    </div>
</template>

<style scoped>
.done {
    text-decoration: line-through;
}
</style>