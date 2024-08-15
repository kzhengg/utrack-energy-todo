<script setup>
import { ref } from "vue";

const todos = ref([]);
const task = ref("");

const addTodo = () => {
  todos.value.push({
    content: task.value,
    done: false,
  });
};
const removeTodo = (todo) => {
  todos.value = todos.value.filter((t) => t !== todo);
};
</script>

<template>
  <section>
    <form @submit.prevent="addTodo">
      <input
        type="text"
        placeholder="e.g. interview with uTrack"
        v-model="task"
      />
      <input type="submit" value="Add task" />
    </form>
  </section>

  <section>
    <h3>TODO LIST</h3>
    <div>
      <div v-for="todo in todos">
        <label>
          <input type="checkbox" v-model="todo.done" />
          <span>{{ todo.content }}</span>
          <button @click="removeTodo(todo)">Delete</button>
        </label>
      </div>
    </div>
  </section>
</template>

<style scoped></style>
