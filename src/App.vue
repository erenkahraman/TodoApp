<template>
  <div class="container">
    <h3 class="text-center">TodoApp</h3>
    <hr>
    <label for="todoText"></label>
    <input 
    @keydown.enter="addNewTodo" 
    type="text" 
    id = "todoText" 
    placeholder="Task ekle"
    >
    <ul>
      <li 
      v-for="todoItem in todoList"
      :key = "todoItem.id " 
      class="d-flex justify-content-between align-items-center">
      <span>{{todoItem.text}}</span>
      <button @click="deleteItem(todoItem)" class="sm red">Sil</button>
      </li>
    </ul>
    <small class="mt-2 d-flex justify-content-end green">#{{todoList.length}} adet task vardır</small>
  </div>
</template>
<script>
export default{
  data(){
    return{
      todoList: [
        {id : 1, text : "task1"},
        {id : 2, text : "task2"},
        {id : 3, text : "task3"},
        {id : 4, text : "task4"},
        {id : 5, text : "task5"},
        {id : 6, text : "task6"},
      ]
    }
  },
  methods : {
    deleteItem(todoItem){
      this.todoList = this.todoList.filter((t) => t != todoItem); 
    },
    addNewTodo(event){
      this.todoList.push({
        id : new Date().getTime(),
        text : event.target.value,
      });
      event.target.value = '';
    },
  },
};
</script>