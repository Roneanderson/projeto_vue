<script setup>
    const props = defineProps(["getNumeroCampo", "getNumeroCampo2", "operador", "resultado"])
</script>
<template>
    <form>
        <div class="row">
            <div class="col">
                <input type="number" @keyup="props.getNumeroCampo" placeholder="Digite o valor 1">
            </div>
            <div class="col-md-3">
                <ul>
                    <select @change="props.operador" class="col-md-3 p-md-1">
                        <option value="adicao">+</option>
                        <option value="subtracao">-</option>
                        <option value="multiplicacao">*</option>
                        <option value="divisao">/</option>
                    </select>
                </ul>
            </div>
            <div class="col">
                <input type="number" @keyup="props.getNumeroCampo2" placeholder="Digite valor 2">
            </div>
        </div>
    </form>
    <ul class="list-group mt-4">
        <li class="list-group-item">
            Resultado: {{ props.resultado }}
        </li>
    </ul>
</template>

<style scoped>
    .done {
        text-decoration: line-through;
    }
</style>