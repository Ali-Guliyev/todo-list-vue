<template>
  <div class="todo" :class="{ completed: todo.completed }">
    <span>{{ todo.body }}</span>
    <div class="icons">
      <i @click="$emit('toggle', todo.id)" class="completed fas fa-check"></i>
      <i @click="$emit('delete', todo.id)" class="delete fas fa-times"></i>
    </div>
  </div>
</template>

<script>
export default {
  props: ["todo"],
  data() {
    return {};
  },
};
</script>
