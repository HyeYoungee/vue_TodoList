<script>
  import Todo from './components/Todo.vue';
  export default{
    components: {
      Todo
    },
    data(){
      return{
        todoText: '',
        todos: [
          {id:1, text:'Learn Web', checked:false},
          {id:2, text:'Get a job', checked:false}
        ]
      }
    },
    methods: {
      AddTodo(e){
        // console.log(e.target.value)
        this.todos.push({
          id: Math.random(),
          text: e.target.value,
          checked: false
        });
        this.todoText = '';
      },
      toggleCheck({id, checked}){
        const index = this.todos.findIndex(todo => todo.id === id);
        this.todos[index].checked = checked;
        console.log(this.todos);
      }
    }
  }
</script>

<template>
  <div class="container mt-5">
    <h1 class="text-center mb-4">Todo App</h1>

    <div class="mb-3">
      <label for="todo" class="form-label">Todo Input</label>
      <input 
        type="text" 
        class="form-control" 
        id="todo" 
        placeholder="할 일을 입력하세요"
        required
        @keyup.enter="AddTodo"
        v-model="todoText"
      >
    </div>

    <Todo v-for="todo in todos" :key="todo.id" :todo="todo" @toggle-checkbox="toggleCheck"/>

  </div>
</template>

<style scoped>

</style>
