<template>
    <div class="todo-item">
        <input v-model="text" type="text">
        <button @click="addTodo">Add</button>
    </div>
</template>

<script lang="ts">
    import {Component, Vue} from 'vue-property-decorator'

    @Component
    export default class TodoItem extends Vue {
        text = ''
        addTodo() {
            this.$emit('addTodo', this.text)
            this.text = ''
        }
    }
</script>

<style scoped lang="scss">

</style>