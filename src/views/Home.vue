<template>
  <div class="home-page">
    <CreateTodo 
    @create-todo="onSubmitClicked"
    /> 
    <div v-if="loading">
      Loading....
    </div>
    <TodoList v-else-if="todos && todos.length" 
    :todos="todos" 
    @remove-todo="onRemovedClicked" 
    />
      <div v-else>
        Список пуст
      </div>
    </div>
</template>

<script>
import TodoList from '@/components/TodoList';
import CreateTodo from '@/components/CreateTodo';
export default {
  name: 'Home',
  components: {
    TodoList,
    CreateTodo
  },
  data: () => ({
    todos: [],
    loading: false,
  }),
  mounted() {
    this.fetchtodos()
  },
  methods: {
    onSubmitClicked(title) {
      if (title != '') {
        let max = 0
        if (this.todos.length != 0) {
          max = this.todos.reduce((acc, curr) => acc.id > curr.id ? acc : curr).id + 1;
        };
        let todo = {
          id: max,
          title: title,
          complited: false,
          userId: 1,
        }
        this.todos.push(todo);
      }
    },
    onRemovedClicked(id) {
        this.todos = this.todos.filter((todo) => todo.id != id);
    },
    async fetchtodos() {
      try {
        this.loading = true;
        const respons = await fetch('https://jsonplaceholder.typicode.com/todos');
        this.todos = await respons.json();  
      } catch (error) {
        
      } finally{
        this.loading = false;
      }
      
    },
  }
}
</script>
