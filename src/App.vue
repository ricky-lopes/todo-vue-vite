<script setup>
import { ref } from 'vue'
import Todo from './components/Todo.vue'
import TodoForm from './components/TodoForm.vue'

  const todos = ref([
    {
      id: 1,
      text: "Treinar",
      category: "Saúde",
      isCompleted: false
    },
    {
      id: 2,
      text: "Arrumar a Casa",
      category: "Obrigações",
      isCompleted: false
    },
    {
      id: 3,
      text: "Estudar Programação",
      category: "Metas",
      isCompleted: false
    },
    {
      id: 4,
      text: "Estudar Inglês",
      category: "Metas",
      isCompleted: false
    },
    {
      id: 5,
      text: "Jogar",
      category: "Lazer",
      isCompleted: false
    },
    {
      id: 6,
      text: "Passear com Cachorro",
      category: "Obrigações",
      isCompleted: false
    }
  ]);

  function addTodo(text, category) {
    const newTodos = [...todos.value, {
      id: Math.floor(Math.random() * 10000),
      text,
      category,
      isCompleted: false
    }];

    todos.value = newTodos;
  }

  const removeTodo = (id) => {
    const newTodos = [...todos.value];
    const filteredTodos = newTodos.filter(todo => todo.id !== id);
    todos.value = filteredTodos;
  }

  const completeTodo = (id) => {
    const newTodos = [...todos.value];
    newTodos.map((todo) => todo.id === id ? todo.isCompleted = !todo.isCompleted : todo);
    todos.value = newTodos;
  }
</script>

<template>
<div className="app">
    <h1>Lista de Tarefas</h1>
    <TodoForm :addTodo="addTodo" />
    <div className="todo-list">
      <div>
        <Todo v-for="todo of todos" :todo="todo" :removeTodo="removeTodo" :completeTodo="completeTodo"/>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>
