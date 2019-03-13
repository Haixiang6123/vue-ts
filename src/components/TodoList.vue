<template>
    <div class="todo-list">
        <ol>
            <li v-for="(todoItem, index) in list" :key="index">
                <input type="checkbox" @change="changeStatus(todoItem, $event)" :checked="todoItem.status === 'done'">
                {{todoItem.name}}
            </li>
        </ol>
    </div>
</template>

<script lang="ts">
    import { Component, Vue } from 'vue-property-decorator'
    import Todo from '../models/Todo'

    @Component({
        props: {
            list: Array
        }
    })
    export default class TodoList extends Vue {
        changeStatus(todoItem: Todo, event: Event) {
            this.$emit('updateTodo', todoItem, {
                status: event.target.checked ? 'done' : 'todo'
            })
        }
    }
</script>

<style scoped lang="scss">
ol {
    padding: 0;
    list-style-type: none;
}
</style>