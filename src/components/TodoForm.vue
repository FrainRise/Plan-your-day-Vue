<template>
  <form class="form-control" @submit.prevent="onSubmit">
        <div class="input-block">
            <label for="todo">Enter your activity: </label>
            <input class="custom-input" id="todo" v-model="todo" /> 
        </div>
        
        <div class="checkbox-block">
            <label for="checkbox" class="checkbox-container">
                Important activity? 
                <input type="checkbox" class="checkbox" id="checkbox" v-model="isImportant" />
                <span class="checkmark"></span>
            </label>
        </div>
        
        <input class="button" type="submit" value="Submit" />
  </form>
</template>

<script>
import { uuid } from 'vue-uuid'

export default {
    name: 'TodoForm',
    data: () => {
        return {    
            todo: '',
            isImportant: false,
            isDone: false,
        }
    },
    methods: {
        onSubmit() {
            if(this.todo === '') {
                alert('Please fill out the fields')
                return;
            }

            let todoObj = {
                id: uuid.v1(),
                todo: this.todo,
                isImportant: this.isImportant,
                isDone: this.isDone,
                date: new Date()
            }

            this.$emit('todo-submition', todoObj)

            this.todo = ''
            this.isImportant = false
            this.isDone = false
        }
    }
}
</script>

<style>
.form-control {
    position: relative;
    margin-bottom: 0.5rem;
}

.input-block {
    margin: 1.5rem 0;
}

.form-control .custom-input{
    outline: none;
    border: 2px solid #ccc;
    display: block;
    width: 95%;
    color: #2c3e50;
    padding: 0.7rem 0.7rem;

    border-radius: 3px;
    font-size: 1rem;
    cursor: pointer;
}


.form-control label {
    display: block;
    float: left;
    text-align: left;
    width: 100%;
    margin: 0.7rem 0;
    font-size: 1.5rem;
    font-weight: 500;
}

.form-control .button {
    width: 30%;
    padding: 0.7rem 0;

    background: transparent;
    color: #42b983;
    border: 1px solid #42b983;
    border-radius: 3px;
    cursor: pointer;

    font-size: 1rem;
    font-weight: bold;
    letter-spacing: 0.1rem;
    text-transform: uppercase;

    transition: all .2s ease-in;
}

.form-control .button:hover {
    color: #000000;
    background: #42b983;
}

.form-control .custom-input:active,
.form-control .custom-input:focus {
    transition: border 0.22s;
    border: 2px solid #42b983;
}

.checkbox-block {
    display: flex;
    justify-content: space-between;
    margin: 1.5rem 0;
    align-items: center;
    align-content: center;
}

.checkbox-container {
  display: block;
  position: relative;
  cursor: pointer;
  font-size: 22px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.checkbox-container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

.checkmark {
  position: absolute;
  top: 0;
  right: 0;
  height: 25px;
  width: 25px;
  border: 1px solid  #ccc;
  background-color: #eee;
}

.checkbox-container:hover input ~ .checkmark {
  background-color: #ccc;
}


.checkbox-container input:checked ~ .checkmark {
  background-color: #42b983;
  border-color: #42b983;
}

.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

.checkbox-container input:checked ~ .checkmark:after {
  display: block;
}

.checkbox-container .checkmark:after {
  right: 9px;
  top: 5px;
  width: 5px;
  height: 10px;
  border: solid white;
  border-width: 0 3px 3px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
}
</style>

