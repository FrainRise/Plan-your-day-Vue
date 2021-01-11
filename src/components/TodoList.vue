<template>
    <div class="container-list" v-if="todoList.length">
        <hr class="divide-line" />
        <h2 class="list-title">List of plans</h2>
        <ul class="list">
            <li 
                class="list-item" 
                :class="{important: todo.isImportant, done: todo.isDone}" 
                v-for="(todo, index) in todoList" 
                :key="index" 
                @click="todo.isDone = !todo.isDone"
            >
                <span class="todo-text">{{index + 1}}. {{ todo.todo }}</span>
                <span 
                    class="data-creation" 
                    :class="{important: todo.isImportant, doneSpan: todo.isDone}"
                >
                    {{ todo.date.toLocaleDateString()}}
                </span> 
                <button 
                    class="btn" 
                    :class="todo.isDone ? 'remove' : 'disable'" 
                    :disabled="!todo.isDone" 
                    @click="removeTodos(index)"
                >remove</button>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'TodoList',
    props: {
        todoList: {
            type: Array,
            required: true
        },
        removeTodos: {
            type: Function,
            required: true
        }
    },
}
</script>

<style>
.container-list{
    text-align: left;
}

.list-title {
    text-align: center;
    text-transform: uppercase;
    margin-bottom: 3.5rem;
}

.list {
    padding: 0;
}

.list .list-item {
    display: flex;
    align-items: center;
    align-content: center;
    margin: 1.1rem 0;
    justify-content: space-between;
    list-style: none;
    font-size: 1.5rem;
    cursor: pointer;
}

.data-creation {
    font-size: 1rem;
    color: #70757c;
}

.important {
    color: red;
}

.done .todo-text, .done span {
    text-decoration: line-through;
    color: #dadada;
    transition: all .2s ease-in;
    flex-wrap: wrap;
}

.todo-text {
    word-wrap: break-word;
}

.btn.disable {
    background: #ececec;
    border-color: #c5c5c5;
    color: #c5c5c5;
}

.doneSpan {
   color: #dadada; 
}

.divide-line {
  margin: 2.5rem 0;
  border: 1px solid rgb(207, 207, 207);
}

.btn {
    color: #42b983;
    border-radius: 99px;
    letter-spacing: 0.05em;
    border: 1px solid #42b983;
    text-transform: uppercase;
    padding: 0.5rem 1.5rem;
    font-weight: 700;
    background: #fff;
    transition: all 0.22s;
    cursor: pointer;
}

.btn.remove {
    background: #e53935;
    color: #fff;
    border-color: #e53935;
    transition: all .5s ease-out;
}

.btn.remove:hover{
    background: transparent;
    color: #e53935;
}
</style>