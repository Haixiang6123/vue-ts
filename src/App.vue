<template>
    <div id="app">
        <new-todo @addTodo="addTodo"></new-todo>
        <todo-list :list="list"></todo-list>
    </div>
</template>

<script lang="ts">
import {Component, Vue} from 'vue-property-decorator';
import TodoList from './components/TodoList'
import NewTodo from './components/NewTodo'

interface Todo {
    name: string
    status: 'done' | 'todo' | 'deleted'
}

@Component({
    components: {
        TodoList,
        NewTodo
    },
})
export default class App extends Vue {
    list: Array<Todo> = [
        {name: 'Do homework', status: 'done'},
        {name: 'Go sleep', status: 'todo'}
    ]

    addTodo(name: String) {
        let todo: Todo = {
            name,
            status: 'todo'
        }
        this.list.push(todo)
    }
}
</script>

<style lang="scss">
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
}
</style>
