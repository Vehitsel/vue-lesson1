<template>
  <div class="home-page">
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
export default {
  name: 'Home',
  components: {
    TodoList
  },
  data: () => ({
    todos: [],
    loading: false,
  }),
  mounted() {
    this.fetchtodos()
  },
  methods: {
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
