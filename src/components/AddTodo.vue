<template>
  <div>
    <form @submit="AddTodo">
      <input type="text" name="title" v-model="title" placeholder="Add Todo.." />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script>
//import uuid from "uuid";
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },

  methods: {
    AddTodo(e) {
      e.preventDefault();
      let newTodo = {
        title: this.title,
        completed: false
      };
      this.title = "";
      //Send up the parent app
      this.$emit("add-todo", newTodo);
    }
  }
};
</script>

<style  scoped>
/*Flexbox */
form {
  display: flex;
}

input[type="text"] {
  flex: 10;
  padding: 5px;
}

input[type="submit"] {
  flex: 2;
}
</style>


