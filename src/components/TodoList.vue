<template>
  <div class="todo-list" v-if="todos.length !== 0">
    <TodoItem
      v-for="todo in todos"
      :key="todo"
      v-bind:todoProps="todo"
      v-on:item-completed="markCompleted"
      @item-deleted="itemDeleted"
    />
    <!-- @ (shorthand) = v-on -->
  </div>

  <div class="empty-message" v-else>
    <h2>Yeah, you don't have any task !</h2>
  </div>
</template>

<script setup>
import { ref } from "@vue/reactivity";
import { watch } from "vue";
import TodoItem from "./TodoItem.vue";
import axios from "axios";
// props:['newItemProps'];
const props = defineProps(["newItemProps"]);

const a = ref(0);
const todos = ref([]);

const getAllTodos = async () => {
  try {
    const response = await axios.get(
      "https://jsonplaceholder.typicode.com/todos?_limit=5"
    );
    console.log(response.data);
    todos.value = response.data;
  } catch (error) {
    console.log(error);
  }
};
getAllTodos();

const markCompleted = (id) => {
  todos.value = todos.value.map((todo) => {
    if (todo.id === id) todo.completed = !todo.completed;
    return todo;
  });
};
const itemDeleted = async (id) => {

  try {
    await axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`);
  todos.value = todos.value.filter((todo) => todo.id !== id);
  } catch (error) {
    console.log(id);
  }
};

const addNewItem = (newItem) => {
  todos.value.unshift(newItem);
};
watch(
  () => props.newItemProps,
  (hehe) => {
    console.log("hehe", hehe);
    if (!todos.value.some((i) => i.id === hehe.id)) {
      addNewItem(hehe);
    }
  },
  { deep: true }
);
watch(a, (newval) => {
  console.log(newval);
});
</script>

<style scoped>
.empty-message {
  text-align: center;
  margin-top: 40px;
  color: rgb(111, 112, 112);
}
</style>
