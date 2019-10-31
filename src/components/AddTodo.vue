<template>
  <div>
    <form @submit="addTodo">
      <input type="text" v-model="title" name="title" placeholder="Add Todo...">
      <input type="submit" value="Submit" class="btn">
    </form>
  </div>
</template>

<script>
//import uuid from "uuid" for without jsonplaceholder

export default {
  name:"AddTodo",
  data(){
    return{
      title:''
    }
  },
  methods:{
    addTodo(e){
      e.preventDefault();
      const newTodo = {
        // id: uuid.v4(), for without jsonplaceholder
        title:this.title,
        completed:false
      }
      // send up to parent
      this.$emit('add-todo',newTodo)
      // clear input field
      this.title = "";
    }
  }
}
</script>

<style scoped>
  form{
    display:felx;
  }

  input[type="text"]{
    flex:10;
    padding:5px;
  }

  input[type="submit"]{
    flex:2;
  }
</style>