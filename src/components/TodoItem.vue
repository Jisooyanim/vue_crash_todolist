<template>
    <div class="todo-item" 
        v-bind:class="{'is-complete':todo.completed}"
    >
        <p>
            <input type="checkbox" v-on:change="markComplete">
            {{todo.title}}
            <button @click="$emit('del-todo', todo.id)" 
            class="del">x</button>
        </p>
    </div>
</template>

<script>
export default{
    name: "TodoItem",
    props: ["todo"],
    data() {
        return {
            todoLocal: this.todo,
        };
    },
    methods: {
        markComplete(){
            //The line below generates an errors due to unexpected mutation. To solve this problem
            //the data can be stored as a local data. Hence, a data() was craeted above. 
            // this.todo.completed = !this.todo.completed 
            
            this.todoLocal.completed = !this.todoLocal.completed;
        }
    }
}
</script>

<style scoped>
    .todo-item{
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
    }

    .is-complete{
        text-decoration: line-through;
    }

    .del{
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
    }
</style>