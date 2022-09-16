<script>
import { ref } from "@vue/reactivity";
import SendIconVue from "./icons/SendIcon.vue";
export default {
  name: "TheWelcome",
  components: { SendIconVue },
  setup(props, context) {
    const title = ref("");

    const handleSubmit = (e) => {
      e.preventDefault();

      const newItem = {
        id: Math.random(),
        title:title.value,
        completed:false,
      }
      if(title.value){
        context.emit('new-item',newItem)
        console.log(context)
      }
      title.value = ''
    };
    

    return { title, handleSubmit };
  },
};
</script>

<template>
  <div class="form-card">
    <p>Enter a task you wanna do ...</p>
    <form @submit="handleSubmit">
      <input type="text" placeholder="Eg: Feed the cat..." v-model="title" />
      <button class="btn btn-primary btn-icon" :disabled="!title.trim().length">
        <span class="icon">
          <SendIconVue />
        </span>
        <span class="text">Submit</span>
      </button>
      <p>Required</p>
    </form>
  </div>
</template>

<style scoped>
h2 {
  margin-bottom: 10px;
}
input {
  margin-right: 10px;
  padding: 10px;
}

.form-card {
  /* border: 1px solid black; */
  border-radius: 10px;
  padding: 20px;
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;
  background-color: #fff;
  position: sticky;
  top: 68.71px;
}
p {
  font-size: 1.1rem;
  margin-bottom: 5px;
}
</style>
