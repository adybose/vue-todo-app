<template>
    <div class="container">
        <div class="row">
            <div class="col-12">
                <p class="display-4">Vue Todo Component</p>
            </div>
        </div>
        <div class="row">
            <p>Add create form</p>
        </div>
        <div class="row">
            <div class="col-12 col-lg-6">
                <ul class="list-group">
                    <!-- <li v-for="(todo, index) in todos"
                    :key="index">{{todo.todoString}}</li> -->
                    <Todo v-for="(todo, index) in todos" 
                    :key="index" 
                    :todoString="todo.todoString" 
                    :completed="todo.completed" 
                    @on-delete="deleteTodo(todo)"
                    @on-toggle="toggleTodo(todo)"
                    />
                </ul>
            </div>
        </div>
    </div>
</template>


<script>
import Todo from "./Todo.vue";

export default {
    components: {
        Todo
    },
    data(){
        return {
            todos: [
                {todoString: "Study Cyberal backend", completed: false},
                {todoString: "Study Cyberal frontend", completed: false},
                {todoString: "Cook dinner", completed: true},
                {todoString: "Study Vue.js", completed: false}
            ]
        };
    },
    methods: {
        addTodo(newTodoString){
            this.todos.push({ // this is the CombinedVueInstance which contains all data, methods, etc. which are accessible to it.
                todoString: newTodoString,
                completed: false
            })
        },
        toggleTodo(todo){
            todo.completed = !todo.completed;
        },
        editTodo(todo, updatedTodoString){
            todo.todoString = updatedTodoString;
        },
        deleteTodo(todoToDelete){
            this.todos = this.todos.filter(todo => todo.todoString !== todoToDelete.todoString)
        }
    }
}
</script>


<style>

</style>