<template>
  <div class="todo-item-wrapper">
    <div :class="['todo-item-title', todoProps.completed ? 'isCompleted' : '']">
     {{todoProps.title}}
    </div>
    <div class="todo-item-action">
      <button
        :class="[
          'btn-icon btn-done',
          todoProps.completed ? 'btn-done-active' : '',
        ]"
        @click="markCompleted"
      >
        <IconDone />
      </button>
      <button class="btn-icon btn-delete" @click="deleteItem">
        <IconDelete />
      </button>
    </div>
  </div>
</template>

<script>
import IconDelete from "./icons/IconDelete.vue";
import IconDone from "./icons/IconDone.vue";
import IconCancel from "./icons/IconCancel.vue";
export default {
  name: "TodoItem",
  props: ["todoProps"],
  components: { IconDelete, IconDone, IconCancel },
  setup(props, context) {
    const markCompleted = () => {
      console.log(props.todoProps.id);
      context.emit("item-completed", props.todoProps.id);
      //   console.log(context);
    };
    const deleteItem = () => {
      console.log(props.todoProps.id);
      context.emit("item-deleted", props.todoProps.id);
      //   console.log(context);
    };
    return {
      markCompleted,
      deleteItem
    };
  },
};
</script>



<style scoped>
.todo-item-wrapper {
  border-radius: 10px;
  padding: 20px;
  margin-bottom: 15px;
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;
  background-color: "#fff";
  display: flex;
  justify-content: space-between;
}
.todo-item-action {
  width: 230px;
  display: flex;
  justify-content: flex-end;
}

.btn-icon {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  cursor: pointer;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border: none;
  margin-right: 5px;
}
.btn-icon:hover {
  background-color: #d1cfcf;
  transition: 0.3s;
}
.btn-delete {
  color: orange;
}
.btn-done {
  color: green;
}
.btn-done-active {
  background-color: #d1cfcf;
}
.isCompleted {
  text-decoration: line-through;
  opacity: 0.4;
}

.effect{
  opacity: 0;
}

.hidden {
  visibility: hidden;
  opacity: 0;
  transition: visibility 0s 2s, opacity 2s linear;
}
/* @keyframes fade-out{
  from {opacity: 1;}
  to {opacity: 0;}
} */

</style>
