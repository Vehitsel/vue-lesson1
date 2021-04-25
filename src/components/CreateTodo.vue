<template>
    <div class="wrapper">
        <input type="text" v-model="title">
        <button @click="$emit('create-todo', title)" class="cr">add</button>
    </div>
</template>

<script>
export default {
    name: 'CreateTodo',
    data: () => ({
        title: ''
    })
}
</script>

<style lang="scss" scoped>
.wrapper {
   display: flex;
   flex-flow: row;
   width: 100%;
   justify-content: center;
   input {
       width: 150px;
   }
   button {
       padding: 8px 22px;
       font-size: 14px;
       border-radius: 12px;
       border: 0;
       outline: none;
       white-space:nowrap;
       background: #42b983;
       color: white;
       cursor: pointer;
       margin-left: 20px;
   }
}
</style>