<template>
    <div class="form-footer" v-if="todoList.length">
        <hr class="divide-line">
        <div class="todos-info">
            <span class="info amount">
                Amount: {{ todoList.length }}
            </span>
            <span class="info important">
                Important: {{ filteredByImportanceFunc }}
            </span>
            <span class="info todo-done">
                Done: {{ filteredByDoneFunc }}
            </span>
        </div>
    </div>
</template>

<script>
export default {
    name: 'FormFooter',
    props: {
        todoList: {
            type: Array,
            required: true
        }
    },
    data: () => {
        return {
            filteredByImportance: []
        }
    },
    computed: {
        filteredByImportanceFunc() {
            return this.todoList.filter(todo => todo.isImportant).length
        },
        filteredByDoneFunc() {
            return this.todoList.filter(todo => todo.isDone).length
        }
    }
}
</script>

<style>
.todos-info {
    display: flex;
    justify-content: space-between;
}

.todos-info .info {
    font-size: 1.25rem;
}

.amount {
    color: #2c3e50;
}

.todo-done {
    color: #34a371!important;
}

</style>
