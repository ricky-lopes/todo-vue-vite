<script setup>
    import { ref } from 'vue';

    defineProps({
        addTodo: {
            type: Function,
            required: true,
        },
    })

    const value = ref("");
    const category = ref("");

    function handleSubmit() {
        window.alert("Preencha todos os campos!");
        return;
    }

    function clearInputs() {
        value.value = "";
        category.value = "";
    }

</script>

<template>
    <div className='todo-form'>
      <h2>Criar Tarefa:</h2>
      <input type="text" v-model="value" placeholder='Digite o título' />
      <select v-model="category">
        <option value="">Selecione uma categoria</option>
        <option value="Saúde">Saúde</option>
        <option value="Obrigações">Obrigações</option>
        <option value="Metas">Metas</option>
        <option value="Lazer">Lazer</option>
      </select>
      <button @click="!value || !category ? handleSubmit() : addTodo(value,category);clearInputs() ">Criar Tarefa</button>
    </div>
</template>