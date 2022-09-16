<!-- <script >
import { ref } from "@vue/reactivity";
import TheWelcome from "../components/TheWelcome.vue";
import TodoList from "../components/TodoList.vue";
export default {
  name: "HomeView",
  components: { TheWelcome, TodoList },
  setup() {
    const newItem = ref(null);
    const handleNewItem = (data) => {
      newItem.value = data;
    };
    return { newItem, handleNewItem };
  },
};

</script> -->

<script setup>
import { ref } from "@vue/reactivity";
import TheWelcome from "../components/TheWelcome.vue";
import TodoList from "../components/TodoList.vue";
const newItem = ref(null);
const handleNewItem = (data) => {
  newItem.value = data;
};
</script>

<template>
  <main>
    <div class="container">
      <div class="form-container">
        <TheWelcome @new-item="handleNewItem" />
      </div>
      <div class="todolist-container">
        <TodoList v-bind:newItemProps="newItem" />
      </div>
    </div>
  </main>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}
.form-container {
}
.todolist-container {
  margin-left: 20px;
  flex: 1;
}
</style>
