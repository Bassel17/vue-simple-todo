<template>
    <div>
        <button class="delete-button" @click="$emit('del-todo',todo.id)">x</button>
        <h3 v-bind:class="{'isCompleted':todo.completed}">{{todo.title}}</h3>
        <input type="checkbox" v-bind:checked="todo.completed" v-on:change="markComplete"/>
    </div>
</template>

<script>
export default {
    name:"TodoItem",
    props:["todo"],
    methods:{
        markComplete(){
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style scoped>
div{
    display:flex;
    align-items: center;
    justify-content: space-between;
    margin:1em;
    padding:1em;
    border: 1px solid aqua;
    background-color: cornsilk;
}

.isCompleted{
    text-decoration: line-through;
}

.delete-button{
    border-radius: 50%;
    width:32px;
    height: 32px;
    background-color:red;
    color:#fff;
}
</style>