<template>
    <div id="app">
        <new-todo @addTodo="addTodo"></new-todo>
        <todo-list :list="list" @updateTodo="updateTodo"></todo-list>
    </div>
</template>

<script lang="ts">
import {Component, Vue} from 'vue-property-decorator';
import TodoList from './components/TodoList'
import NewTodo from './components/NewTodo'
import Todo from './models/Todo'

@Component({
    components: {
        TodoList,
        NewTodo
    },
    watch: {
        list(newValue: Array<Todo>) {
            localStorage.setItem('data', JSON.stringify(newValue))
        }
    }
})
export default class App extends Vue {
    list: Array<Todo> = localStorage.getItem('data') ? JSON.parse(<string>localStorage.getItem('data')) : []

    addTodo(name: string) {
        let todo: Todo = {
            name,
            status: 'todo'
        }
        this.list.push(todo)
    }
    updateTodo(todo: Todo, part: Partial<Todo>) {
        let index: number = this.list.indexOf(todo)
        console.log(index)
        let newTodo: Todo = Object.assign({}, todo, part)
        console.log(newTodo)
        this.list.splice(index, 1, newTodo)
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
