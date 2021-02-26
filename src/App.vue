<template>
  <section>
    <TodoList />
    <router-view />
  </section>
</template>

<script>
import TodoList from "./views/TodoList.vue";

export default {
  components: {
    TodoList,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Akaya+Telivigala&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@200;300&display=swap");

:root {
  --dark-blue: #2f3749;
  --blue: #1f71f5;
  --main-blue: #4c90fd;
  --hover-blue: #3c72ca;
  --todo: #5792f0;
  --todo-completed: #3c7be09c;
}

section {
  display: flex;
  align-items: center;
  flex-direction: column;
  margin: 0;
  padding: 0;
}

.title {
  font-family: "Akaya Telivigala", cursive;
  font-size: 80px;
  margin: 10px;
  background: linear-gradient(to bottom right, var(--blue), var(--dark-blue));
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
}

.title::after {
  content: "";
  width: 280px;
  height: 6px;
  transform: translate(-50%, 85px);
  position: absolute;
  left: 50%;
  background: linear-gradient(to right, var(--blue), var(--dark-blue));
}

.todo-input {
  margin: 6px 0 10px 0;
  padding: 8px 13px;
  border: none;
  border-radius: 12px;
  outline: none;
  background-color: var(--main-blue);
}

.todo-input:focus,
.add-btn:hover {
  background-color: var(--hover-blue);
}

.todo-input::placeholder,
.todo-input,
.add-btn {
  color: white;
}

.add-btn,
.todo-input {
  font-size: 25px;
  background-color: var(--main-blue);
  border: none;
  outline: none;
  border-radius: 12px;
  transition: all 0.3s ease;
}

.add-btn {
  padding: 8px 11px;
  cursor: pointer;
  margin-left: 5px;
}
</style>
