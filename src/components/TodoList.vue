<template>
  <div>
    <div class="todo-input-container mb-4">
      <input
        type="text"
        class="input"
        v-model="newTodo"
        @keyup.enter="addTodo"
        placeholder="What needs to be done?"
      />
      <button type="sumbit" class="btn btn-primary ml-5" @click="addTodo">Add Todo</button>
    </div>
    <hr />
    <ul :key="todo.id" v-for="(todo, index) in todos">
      <li class="todo-item">
        <div class="todo-text">
          <p class="todo-item-text" v-if="!todo.editing" @dblclick="editTodo(todo)">
            {{
            todo.text
            }}
          </p>
          <input
            type="text"
            class="input"
            v-else
            v-model="todo.text"
            @blur="editComplete(todo)"
            @keyup.enter="editComplete(todo)"
            v-focus
          />
        </div>
        <button class="btn btn-danger" @click="removeTodo(index)">&times;</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'todo-list',
  data() {
    return {
      newTodo: '',
      idForTodo: 2,
      todos: [
        {
          id: 1,
          text: 'Finish up some VUE tuts',
          isCompleted: false,
          editing: false,
        },
      ],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim().length === 0) {
        return;
      }
      this.todos.push({
        id: this.idForTodo,
        text: this.newTodo,
        isCompleted: false,
        editing: false,
      });
      this.idForTodo += 1;
      this.newTodo = '';
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
    /* eslint-disable no-param-reassign */
    editTodo(todo) {
      todo.editing = true;
    },
    /* eslint-disable no-param-reassign */
    editComplete(todo) {
      todo.editing = false;
    },
  },
  directives: {
    focus: {
      inserted(el) {
        el.focus();
      },
    },
  },
};
</script>

<style>
.input {
  width: 300px;
  border: none;
  background-color: #eee;
}

hr {
  display: block;
  height: 1px;
  border: 0;
  border-top: 1px solid #333;
  margin: 1em 0;
  padding: 0;
}

.todo-item {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-end;
}

.todo-input-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

p {
  margin: 0;
  padding-top: 1rem;
}

ul p {
  cursor: pointer;
}
</style>
