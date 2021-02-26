<template>
  <h1 class="title">Todo List</h1>
  <form @submit.prevent="addTodo" class="add-todo-form">
    <input
      v-model="input"
      class="todo-input"
      type="input"
      placeholder="Add a todo..."
    />
    <button type="submit" class="add-btn">
      <i class="fas fa-plus"></i>
    </button>
  </form>
  <div class="todo-list">
    <Todo
      @toggle="toggleCompleted"
      @delete="deleteTodo"
      v-for="todo in todos"
      :key="todo"
      :todo="todo"
    />
  </div>
</template>

<script>
import Todo from "./Todo.vue";

export default {
  components: { Todo },
  data() {
    return {
      todos: [
        // { id: 1, body: "Do something", completed: false },
        // { id: 2, body: "Do programming", completed: true },
        // { id: 3, body: "Go to work", completed: false },
      ],
      input: "",
    };
  },
  methods: {
    toggleCompleted(id) {
      let todo = this.todos[id - 1];
      todo.completed = !todo.completed;
    },
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id != id);

      for (let i = 0; i < this.todos.length; i++) {
        this.todos[i].id = i + 1;
        console.log(this.todos);
      }
    },
    addTodo() {
      if (this.input) {
        for (var i = 0; i < this.todos.length; i++) {
          this.todos[i].id += 1;
        }

        this.todos.unshift({
          id: 1,
          body: this.input,
          completed: false,
        });

        this.input = "";
      }
    },
  },
};
</script>

<style>
.todo {
  background-color: var(--todo);
  color: white;
  font-family: "Poppins", sans-serif;
  font-size: 20px;
  margin: 10px;
  padding: 6px 13px;
  border-radius: 12px;
  display: flex;
  justify-content: space-between;
  transition: all 0.3s ease;
  width: 300px;
}

@keyframes fadeIn {
  100% {
    font-size: 5px;
    opacity: 0%;
    width: 200px;
  }
}

.icons * {
  cursor: pointer;
  margin-left: 10px;
  font-size: 22px;
  transition: all 0.1s ease;
}

.icons *:hover {
  transform: scale(1.25);
}

.icons .completed {
  color: rgb(33, 225, 33);
}

.icons .delete {
  color: rgb(204, 44, 44);
}

.todo.completed {
  background-color: var(--todo-completed);
}

.todo.completed span {
  text-decoration: line-through;
}

.todo.completed .icons .completed {
  color: rgb(58, 212, 58);
}
</style>
