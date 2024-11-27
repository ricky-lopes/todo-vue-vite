<script setup>
  defineProps({
    todo: Object,
    removeTodo: Function,
    completeTodo: Function
  })

</script>

<template>
  <div className="todo" :style="{textDecoration: todo.isCompleted ? 'line-through' : ''}">
    <div className="content">
      <p>{{todo.text}}</p>
      <p className="category">
        ({{todo.category}})
      </p>
    </div>
    <div>
      <button className='complete' @click="completeTodo(todo.id)">Completar</button>
      <button className='remove' @click="removeTodo(todo.id)">X</button>
    </div>
  </div>
</template>

<style scoped>

</style>
